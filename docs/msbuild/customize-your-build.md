---
title: Personalizzare la compilazione | Microsoft Docs
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c52c6b584db94ff3cbe8dc041c00ebe969c9faf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288936"
---
# <a name="customize-your-build"></a>Personalizzare la compilazione

I progetti MSBuild che usano il processo di compilazione standard, vale a dire l'importazione di *Microsoft.Common.props* e *Microsoft.Common.targets*, possono usare diversi hook di estensibilità per personalizzare il processo di compilazione.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Aggiungere argomenti alle chiamate di MSBuild da riga di comando per il progetto

Il file *Directory.Build.rsp* contenuto nella directory di origine o in una directory superiore viene applicato alle compilazioni da riga di comando del progetto. Per informazioni dettagliate, vedere [File di risposta MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props e Directory.Build.targets

Nelle versioni di MS Build precedenti alla 15, per specificare una nuova proprietà personalizzata per i progetti nella soluzione, è necessario aggiungere manualmente un riferimento a tale proprietà per ogni file di progetto della soluzione. In alternativa, era necessario definire la proprietà in un file con *estensione Props* e quindi importare in modo esplicito il file *. props* in ogni progetto della soluzione, tra le altre cose.

Ora è tuttavia possibile aggiungere una nuova proprietà a ogni progetto in un unico passaggio, definendola in un singolo file denominato *Directory.Build.props* nella cartella radice che contiene l'origine. Quando si esegue MSBuild, *Microsoft. Common. props* cerca la struttura di directory per il file *Directory. Build. props* (e *Microsoft. Common. targets* Cerca *Directory. Build. targets*). Se trova la struttura, importa la proprietà. *Directory. Build. props* è un file definito dall'utente che fornisce le personalizzazioni per i progetti in una directory.

> [!NOTE]
> I file system basati su Linux fanno distinzione tra maiuscole e minuscole. Assicurarsi che le maiuscole e minuscole del nome file Directory.Build.props corrispondano esattamente o il file non verrà rilevato durante il processo di compilazione.
>
> Per altre informazioni, vedere [questo problema in GitHub](https://github.com/dotnet/core/issues/1991#issue-368441031).

### <a name="directorybuildprops-example"></a>Esempio di Directory.Build.props

Ad esempio, per consentire a tutti i progetti di accedere alla nuova funzionalità di Roslyn **/deterministic** (esposta nella destinazione `CoreCompile` di Roslyn dalla proprietà `$(Deterministic)`), è possibile eseguire le operazioni indicate di seguito.

1. Creare un nuovo file nella radice del repository denominato *Directory.Build.props*.
2. Aggiungere al file il seguente codice XML.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Eseguire MSBuild. Le importazioni esistenti del progetto di *Microsoft.Common.props* e *Microsoft.Common.targets* trovano il file e lo importano.

### <a name="search-scope"></a>Ambito di ricerca

Quando cerca un file *Directory.Build.props*, MSBuild scorre la struttura di directory verso l'alto a partire dalla posizione del progetto (`$(MSBuildProjectFullPath)`), fermandosi quando individua un file *Directory.Build.props*. Ad esempio, se `$(MSBuildProjectFullPath)` è *c:\users\nomeutente\code\test\case1*, MSBuild inizia a cercare da quel punto ed esegue la ricerca nella struttura di directory verso l'alto finché non trova un file *Directory.Build.props*, come nella struttura di directory riportata di seguito.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

La posizione del file della soluzione è irrilevante per *Directory.Build.props*.

### <a name="import-order"></a>Ordine di importazione

*Directory.Build.props* viene importato molto presto in *Microsoft.Common.props* e le proprietà definite in un secondo tempo non sono disponibili per questo file. Quindi, evitare di fare riferimento a proprietà che non sono ancora state definite (e verranno restituite come vuote).

Le proprietà impostate in *Directory. Build. props* possono essere sostituite altrove nel file di progetto o nei file importati, quindi è necessario considerare le impostazioni in *Directory. Build. props* come specificare i valori predefiniti per i progetti.

*Directory. Build. targets* viene importato da *Microsoft. Common. targets* dopo l'importazione dei file con *estensione targets* dai pacchetti NuGet. Consente quindi di eseguire l'override di proprietà e destinazioni definite nella maggior parte della logica di compilazione oppure di impostare le proprietà per tutti i progetti indipendentemente dai singoli progetti impostati.

Quando è necessario impostare una proprietà o definire una destinazione per un singolo progetto che esegue l'override di qualsiasi impostazione precedente, inserire la logica nel file di progetto dopo l'importazione finale. Per eseguire questa operazione in un progetto di tipo SDK, è necessario innanzitutto sostituire l'attributo di tipo SDK con le importazioni equivalenti. Vedere [come usare gli SDK di progetto di MSBuild](how-to-use-project-sdk.md).

> [!NOTE]
> Il motore MSBuild legge tutti i file importati durante la valutazione, prima di avviare l'esecuzione della compilazione per qualsiasi progetto (incluso qualsiasi `PreBuildEvent` ), quindi questi file non devono essere modificati da `PreBuildEvent` o da qualsiasi altra parte del processo di compilazione. Eventuali modifiche non diventano effettive fino alla successiva chiamata di *MSBuild.exe* o alla successiva compilazione di Visual Studio.

### <a name="use-case-multi-level-merging"></a>Caso d'uso: unione a più livelli

Si supponga di avere questa struttura della soluzione standard:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Potrebbe essere preferibile usare proprietà comuni per tutti i progetti *(1)*, proprietà comuni per i progetti *src**(2-src)* e proprietà comuni per i progetti *test**(2-test)*.

Per consentire a MSBuild di unire correttamente i file "interni"(*2-src* e *2-test*) e il file "esterno" (*1*), è necessario tenere presente che quando MSBuild trova un file *Directory.Build.props*, interrompe l'analisi. Per continuare l'analisi e completare l'unione con il file esterno, inserire questo codice in entrambi i file interni:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

L'approccio generale di MSBuild può essere riepilogato come segue:

- Per ogni progetto, MSBuild trova il primo file *Directory.Build.props* procedendo verso l'alto nella struttura della soluzione, lo unisce ai valori predefiniti e interrompe l'analisi
- Se si desidera trovare e unire più livelli, [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) visualizzare il file "esterno" dal file "interno" (sopra)
- Se il file "esterno" non importa a sua volta un elemento situato a un livello superiore, l'analisi si interrompe qui
- Per controllare il processo di analisi/unione, usare `$(DirectoryBuildPropsPath)` e `$(ImportDirectoryBuildProps)`

O più semplicemente: il primo file *Directory.Build.props* che non esegue alcuna importazione è il punto in cui MSBuild si arresta.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Scegliere se aggiungere proprietà a un file con estensione props o target

MSBuild si basa sull'ordine di importazione e l'ultima definizione di una proprietà (o un `UsingTask` o una destinazione) diventa l'ultima definizione usata.

Quando si usano importazioni esplicite, è possibile importare da un file *.props* o *.targets* in qualsiasi momento. Di seguito è illustrata la convenzione più diffusa:

- I file con estensione *props* vengono importati nella fase iniziale e sono inclusi nell'ordine di importazione.

- I file con estensione *targets* vengono importati nelle fasi conclusive e sono inclusi nell'ordine di compilazione.

Questa convenzione viene applicata dai processi di importazione `<Project Sdk="SdkName">` (ovvero, per prima cosa viene eseguita l'importazione di *Sdk.props*, prima di tutti i contenuti del file, e quindi viene importato *Sdk.targets*, dopo tutti i contenuti del file).

Prima di decidere a quale tipo di file aggiungere le proprietà, usare le linee guida generali seguenti:

- Per molte proprietà, non è importante la posizione in cui vengono definite, in quanto non vengono sovrascritte e, in fase di esecuzione, sono di sola lettura.

- Nel caso in cui sia necessario personalizzare il comportamento in un singolo progetto, impostare i valori predefiniti nel file *props*.

- Evitare di impostare proprietà dipendenti nei file *props* leggendo il valore di una proprietà potenzialmente personalizzata, poiché la personalizzazione verrà eseguita solo nel momento in cui MSBuild leggerà il progetto dell'utente.

- Impostare proprietà dipendenti nei file *targets*, poiché acquisiranno le personalizzazioni dai singoli progetti.

- Se è necessario eseguire l'override delle proprietà, eseguire questa operazione in un file *targets*, dopo che sarà stato possibile applicare tutte le personalizzazioni dei progetti definiti dagli utenti. Prestare attenzione quando si usano proprietà derivate, poiché potrebbe essere necessario eseguire l'override anche di esse.

- Includere elementi nei file *props* (usando una condizione basata su una proprietà). Tutte le proprietà verranno considerate prima di qualsiasi elemento, in modo che vengano applicate tutte le personalizzazioni di proprietà definite nei progetti definiti dagli utenti e in questi sia quindi possibile eseguire l'operazione `Remove` o `Update` su qualsiasi elemento aggiunto tramite l'importazione.

- Definire le destinazioni nei file *targets*. Se, tuttavia, il file *targets* viene importato da un SDK, l'esecuzione dell'override della destinazione risulterà più difficile, poiché nel progetto dell'utente non è disponibile una posizione predefinita in cui eseguirne l'override.

- Se possibile, personalizzare le proprietà in fase di valutazione anziché modificarle all'interno di una destinazione. In questo modo, infatti, risulterà più facile caricare un progetto e seguirne l'andamento.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Per impostazione predefinita, *Microsoft.Common.props* importa `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` e *microsoftcommon.targets* importa `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. Il valore predefinito di `MSBuildProjectExtensionsPath` è `$(BaseIntermediateOutputPath)`, `obj/`. NuGet usa questo meccanismo per fare riferimento alla logica di compilazioni nei pacchetti. In fase di ripristino crea quindi file `{project}.nuget.g.props` che si riferiscono al contenuto del pacchetto.

È possibile disabilitare questo meccanismo di estendibilità impostando la proprietà `ImportProjectExtensionProps` su `false` in un file *Directory.build.props* o prima di importare *Microsoft.Common.props*.

> [!NOTE]
> Disabilitando le importazioni di MSBuildProjectExtensionsPath, la logica di compilazione nei pacchetti NuGet non sarà applicata al progetto. Per eseguire la propria funzione, alcuni pacchetti NuGet richiedono la logica di compilazione. Viene quindi eseguito il rendering se non è disabilitato.

## <a name="user-file"></a>File con estensione user

*Microsoft.Common.CurrentVersion.targets* importa `$(MSBuildProjectFullPath).user` se esiste. In questo modo è possibile creare un file accanto al progetto con tale estensione aggiuntiva. In caso di modifiche a lungo termine che saranno verificate nel controllo del codice sorgente, è preferibile modificare il progetto stesso. In questo modo i gestori futuri non dovranno necessariamente conoscere questo meccanismo di estensione.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath e MSBuildUserExtensionsPath

> [!WARNING]
> Tramite questi meccanismi di estensione è più difficile ripetere le compilazioni su più computer. Provare a usare una configurazione che può verificata nel sistema di controllo del codice sorgente e condivisa tra tutti gli sviluppatori della codebase.

Per convenzione, molti file logici di compilazione importano

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

prima del contenuto e

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

dopo. In questo modo, gli SDK installati possono espandere la logica di compilazione di tipi di progetto comuni.

La stessa struttura di directory viene ricercata in `$(MSBuildUserExtensionsPath)`, vale a dire la cartella *%LOCALAPPDATA%\Microsoft\MSBuild* per ogni utente. I file in tale cartella saranno importati per tutte le compilazioni del tipo di progetto corrispondente, eseguito con le credenziali dell'utente interessato. Per disabilitare le estensioni utente, impostare le proprietà denominate in base al file di importazione nel criterio `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`. Ad esempio, se `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` viene impostato su `false` l'importazione di `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` non sarà eseguita.

## <a name="customize-the-solution-build"></a>Personalizzare la compilazione della soluzione

> [!IMPORTANT]
> Questa procedura di personalizzazione della compilazione della soluzione si applica solo alle compilazioni da riga di comando con *MSBuild.exe*. **Non** si applica alle compilazioni in Visual Studio. Per questo motivo, non è consigliabile applicare la personalizzazione a livello di soluzione. Un'alternativa migliore per personalizzare tutti i progetti in una soluzione consiste nell'usare i file *Directory. Build. props* e *Directory. Build. targets* nella cartella della soluzione, come descritto in precedenza in questo articolo.

Quando MSBuild compila un file della soluzione, prima lo converte internamente in un file di progetto e poi lo compila. Il file di progetto generato importa `before.{solutionname}.sln.targets` prima di definire tutte le destinazioni e `after.{solutionname}.sln.targets` dopo avere importato le destinazioni, incluse le destinazioni installate nelle directory `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` e `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter`.

Ad esempio, è possibile definire una nuova destinazione per scrivere un messaggio di log personalizzato dopo la compilazione di *MyCustomizedSolution.sln* creando un file nella stessa directory denominata *after.MyCustomizedSolution.sln.targets* contenente

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

La compilazione della soluzione è separata dalle compilazioni del progetto, quindi le impostazioni non influiscono sulle compilazioni di progetto.

## <a name="customize-all-net-builds"></a>Personalizzare tutte le compilazioni .NET

Quando si gestisce un server di compilazione, potrebbe essere necessario configurare le impostazioni di MSBuild globalmente per tutte le compilazioni nel server.  In linea di principio, è possibile modificare i file Global *Microsoft. Common. targets* o *Microsoft. Common. props* , ma esiste un modo migliore. È possibile influire su tutte le compilazioni di un determinato tipo di progetto, ad esempio tutti i progetti C#, usando determinate proprietà di MSBuild e aggiungendo determinati `.targets` file e personalizzati `.props` .

Per influire su tutte le compilazioni C# o Visual Basic gestite da un'installazione di MSBuild o Visual Studio, creare un file *Custom. before. Microsoft. Common. targets* o *Custom. after. Microsoft. Common. targets* con destinazioni che verranno eseguite prima o dopo *Microsoft. Common. targets*oppure un file *Custom. before. Microsoft. Common* . props o *Custom. after. Microsoft.* Common. props con proprietà che verranno elaborate prima o dopo Microsoft. Common *.* Props

È possibile specificare i percorsi di questi file usando le proprietà MSBuild seguenti:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- CustomAfterMicrosoftCSharpProps
- CustomAfterMicrosoftVisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

Le versioni *comuni* di queste proprietà influiscono sui progetti C# e Visual Basic. È possibile impostare queste proprietà nella riga di comando di MSBuild.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

L'approccio migliore dipende dallo scenario. Con l'estendibilità di Visual Studio, è possibile personalizzare il sistema di compilazione e fornire un meccanismo per l'installazione e la gestione delle personalizzazioni.

Se si dispone di un server di compilazione dedicato e si desidera assicurarsi che determinate destinazioni vengano sempre eseguite su tutte le compilazioni del tipo di progetto appropriato eseguito su tale server, è opportuno utilizzare un `.targets` file o personalizzato globale `.props` .  Se si desidera che le destinazioni personalizzate vengano eseguite solo quando si applicano determinate condizioni, utilizzare un altro percorso di file e impostare il percorso di tale file impostando la proprietà MSBuild appropriata nella riga di comando di MSBuild solo quando necessario.

> [!WARNING]
> Visual Studio USA i `.targets` file personalizzati `.props` se li trova nella cartella MSBuild ogni volta che compila qualsiasi progetto del tipo corrispondente. Questa operazione può avere conseguenze impreviste e, se eseguita in modo non corretto, può disabilitare la capacità di Visual Studio di essere compilata nel computer.

## <a name="customize-c-builds"></a>Personalizzare le compilazioni C++

Per i progetti C++, i file Custom *. targets* e *. props* indicati in precedenza non possono essere usati nello stesso modo per eseguire l'override delle impostazioni predefinite. *Directory. Build. props* viene importato da *Microsoft. Common. props*, che viene importato in `Microsoft.Cpp.Default.props` mentre la maggior parte dei valori predefiniti è definita in *Microsoft. cpp. props* e per diverse proprietà non è possibile usare una condizione "se non ancora definita", perché la proprietà è già definita, ma il valore predefinito deve essere diverso per determinate proprietà del progetto definite in `PropertyGroup` con `Label="Configuration"` (vedere la struttura dei file con estensione [vcxproj e Props](/cpp/build/reference/vcxproj-file-structure))

Tuttavia, è possibile usare le proprietà seguenti per specificare i file *. props* da importare automaticamente prima/dopo * \* Microsoft. cpp.* Files:

- ForceImportAfterCppDefaultProps
- ForceImportBeforeCppProps
- ForceImportAfterCppProps
- ForceImportBeforeCppTargets
- ForceImportAfterCppTargets

Per personalizzare i valori predefiniti delle proprietà per tutte le compilazioni C++, creare un altro file *. props* (ad indicare, Props *. props*) e definire la `ForceImportAfterCppProps` Proprietà in `Directory.Build.props` che punta a essa:

<PropertyGroup><ForceImportAfterCppProps>$ (MsbuildThisFileDirectory) \MyProps.props<ForceImportAfterCppProps>
</PropertyGroup>

Props *. props* viene importato automaticamente alla fine di *Microsoft. cpp. props*.

## <a name="customize-all-c-builds"></a>Personalizzare tutte le compilazioni C++

Non è consigliabile personalizzare l'installazione di Visual Studio, perché non è facile tenere traccia di tali personalizzazioni, ma se si estende Visual Studio per personalizzare le compilazioni C++ per una determinata piattaforma, è possibile creare `.targets` file per ogni piattaforma e inserirli nelle cartelle di importazione appropriate per tali piattaforme come parte di un'estensione di Visual Studio.

Il `.targets` file per la piattaforma Win32, *Microsoft. cpp. Win32. targets*, contiene l' `Import` elemento seguente:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

È presente un elemento analogo alla fine dello stesso file:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Sono presenti elementi di importazione simili per altre piattaforme di destinazione in *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v {Version} \ piattaforme \* .

Una volta inserito il `.targets` file nella cartella appropriata in `ImportAfter` base alla piattaforma, MSBuild importa il file in ogni compilazione C++ per tale piattaforma. Se necessario, è possibile inserire più `.targets` file. 

Con l'estendibilità di Visual Studio sono possibili altre personalizzazioni, ad esempio la definizione di una nuova piattaforma. Per altre informazioni, vedere [estensibilità del progetto C++](../extensibility/visual-cpp-project-extensibility.md).

### <a name="specify-a-custom-import-on-the-command-line"></a>Specificare un'importazione personalizzata nella riga di comando

Per l' `.targets` oggetto personalizzato che si desidera includere per una compilazione specifica di un progetto C++, impostare una o entrambe le proprietà `ForceImportBeforeCppTargets` e `ForceImportAfterCppTargets` nella riga di comando.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Per un'impostazione globale (per avere effetto su tutte le compilazioni C++ per una piattaforma in un server di compilazione), sono disponibili due metodi. In primo luogo, è possibile impostare queste proprietà usando una variabile di ambiente di sistema sempre impostata. Questa operazione funziona perché MSBuild legge sempre l'ambiente e crea o esegue l'override delle proprietà per tutte le variabili di ambiente.

## <a name="see-also"></a>Vedere anche

- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)

- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
