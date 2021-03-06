---
title: Aggiornare un'Visual Studio predefinita
description: Informazioni su come aggiornare l'estensione Visual Studio per l'utilizzo con Visual Studio 2022.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 512e9a71cde5ca29c737c1623aa0c8f9c37dd60d
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046131"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Aggiornare un'estensione Visual Studio per Visual Studio 2022

> [!IMPORTANT]
> Il consiglio di questa guida è destinato agli sviluppatori nella migrazione di estensioni che richiedono modifiche importanti per funzionare sia nel Visual Studio 2019 che nel 2022. In questi casi è consigliabile avere due progetti VSIX e la compilazione condizionale.
> Molte estensioni saranno in grado di funzionare sia Visual Studio 2019 che 2022 con modifiche secondarie che non richiederanno di seguire i consigli sulla modernizzazione dell'estensione in questa guida.
> Provare l'estensione in Visual Studio 2022 e valutare l'opzione migliore per l'estensione.

È possibile aggiornare l'estensione per l'Visual Studio 2022 Preview seguendo questa guida. Visual Studio 2022 Preview è un'applicazione a 64 bit e introduce alcune modifiche di rilievo in VS SDK. Questa guida illustra i passaggi necessari per far funzionare l'estensione con l'anteprima corrente di Visual Studio 2022, in modo che l'estensione possa essere pronta per l'installazione da parte degli utenti prima che Visual Studio 2022 raggiunga ga.

## <a name="installing"></a>Installazione

Installare Visual Studio 2022 Preview [da Visual Studio 2022 Preview download](https://visualstudio.microsoft.com/vs/preview/vs2022).

### <a name="extensions-written-in-a-net-language"></a>Estensioni scritte in un linguaggio .NET

L'SDK di Visual Studio Visual Studio 2022 per le estensioni gestite è *disponibile esclusivamente* in NuGet:

- Il meta-pacchetto [Microsoft.VisualStudio.Sdk](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (versioni 17.x) include la maggior parte o tutti gli assembly di riferimento necessari.
- È necessario fare riferimento al pacchetto [Microsoft.VSSDK.BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (versioni 17.x) dal progetto VSIX in modo che possa compilare un pacchetto VSIX conforme a Visual Studio 2022.

Le *estensioni* devono essere compilate con la piattaforma "Any CPU" o "x64". La piattaforma "x86" non è compatibile Visual Studio processo a 64 bit di Visual Studio 2022.

### <a name="extensions-written-in-c"></a>Estensioni scritte in C++

Vs SDK per le estensioni compilate con C++ è disponibile con il Visual Studio SDK installato, come di consueto.

Le *estensioni devono* essere compilate in modo specifico Visual Studio SDK 2022 e per amd64.

### <a name="update-your-extension-to-visual-studio-2022"></a>Aggiornare l'estensione a Visual Studio 2022

#### <a name="extensions-with-running-code"></a>Estensioni con codice in esecuzione

Le estensioni con codice *in esecuzione* devono essere compilate in modo specifico per Visual Studio 2022. Visual Studio 2022 non carica alcuna estensione che non ha come destinazione Visual Studio 2022 in modo specifico.

Informazioni su come eseguire la migrazione delle estensioni Visual Studio 2022 a Visual Studio 2022:

1. [Modernizzare i progetti](#modernize-your-vsix-project).
1. [Eseguire il refactoring del codice](#use-shared-projects-for-multi-targeting) sorgente in un progetto condiviso per consentire la destinazione Visual Studio 2022 e versioni precedenti.
1. Aggiungere un Visual Studio progetto VSIX di destinazione [2022](#add-a-visual-studio-2022-target)e la tabella di [remapping pacchetto/assembly.](migrated-assemblies.md)
1. [Apportare le modifiche necessarie al codice.](#handle-breaking-api-changes)
1. [Test dell'Visual Studio 2022.](#test-your-extension)
1. [Pubblicazione dell'Visual Studio 2022.](#publish-your-extension)

#### <a name="extensions-without-running-code"></a>Estensioni senza eseguire codice

Le estensioni che non contengono codice in esecuzione (ad  esempio, modelli di progetto/elemento) non sono necessarie per seguire i passaggi precedenti, inclusa la produzione di due VSIX distinti.

Al contrario, l'unico VSIX deve essere modificato in modo che il `source.extension.vsixmanifest` relativo file dichiari due destinazioni di installazione, come illustrato di seguito:

```xml
<Installation>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0,17.0)">
      <ProductArchitecture>x86</ProductArchitecture>
   </InstallationTarget>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
</Installation>
```

È possibile ignorare i passaggi descritti in questo articolo sull'uso di progetti condivisi e più VSIX. È possibile procedere con [il test](#test-your-extension)di .

> [!NOTE]
> Se si crea una nuova estensione *Visual Studio,* usando Visual Studio 2022 Preview e si vuole (anche) scegliere come destinazione Visual Studio 2019 o una versione precedente, vedere questa [guida.](target-previous-versions.md)

### <a name="msbuild-tasks"></a>MSBuild (attività)

Se si creano attività MSBuild, tenere presente che in Visual Studio 2022 è molto più probabile che verranno caricate in un processo MSBuild.exe a 64 bit. Se l'attività richiede un processo a 32 bit per l'esecuzione, fare riferimento a questa documentazione di [MSBuild](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) per assicurarsi che MSBuild sia in grado di caricare l'attività in un processo a 32 bit.

## <a name="modernize-your-vsix-project"></a>Modernizzare il progetto VSIX

Prima di aggiungere il Visual Studio 2022 all'estensione, è consigliabile prendere questo tempo per pulire e modernizzare il progetto esistente prima di procedere ulteriormente, tra cui:

1. [Eseguire la migrazione da `PackageReference` packages.config a ](/nuget/consume-packages/migrate-packages-config-to-package-reference).

1. Sostituire tutti i riferimenti all'assembly diretto di VS SDK con elementi PackageReference.

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > È possibile sostituire *molti riferimenti* ad assembly con *un solo* PackageReference al metapacchetto:
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" Version="..." />
   >```

   Assicurarsi di selezionare le versioni del pacchetto che corrispondono alla versione minima Visual Studio destinazione.

   Alcuni assembly che non sono univoci per VS SDK (ad esempio, Newtonsoft.Json.dll) possono essere stati individuabili tramite un riferimento semplice prima di Visual Studio 2022, ma in Visual Studio 2022 richiede invece un riferimento al pacchetto perché in Visual Studio 2022 vengono rimosse alcune directory di runtime e SDK di Visual Studio dal percorso di ricerca degli assembly predefinito di `<Reference Include="Newtonsoft.Json" />` MSBuild.

   Quando si passa dai riferimenti di assembly diretti ai riferimenti ai pacchetti NuGet, è possibile che si prelevino altri riferimenti ad assembly e pacchetti analizzatori a causa dell'installazione automatica da parte di NuGet della chiusura transitiva delle dipendenze. Questo è in genere OK, ma potrebbe causare la segnalazione di altri avvisi durante la compilazione. Esaminare questi avvisi e risolvere il maggior numero possibile di avvisi e valutare la possibilità di eliminare gli avvisi che non è possibile risolvere usando aree nel `#pragma warning disable <id>` codice.

## <a name="use-shared-projects-for-multi-targeting"></a>Usare progetti condivisi per la multi-destinazione

[I progetti](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) condivisi sono un tipo di progetto introdotto in Visual Studio 2015. I progetti condivisi in Visual Studio file di codice sorgente possono essere condivisi tra più progetti e compilati in modo diverso usando simboli di compilazione condizionale e set univoci di riferimenti.

Poiché Visual Studio 2022 richiede un set distinto di assembly di riferimento di tutte le versioni precedenti di Visual Studio, le linee guida sono l'uso di progetti condivisi per usare in modo pratico più destinazione l'estensione a pre-Visual Studio 2022 e Visual Studio 2022 (e versioni successive), offrendo la condivisione del codice, ma riferimenti distinti.

Nel contesto delle estensioni Visual Studio, è possibile avere un progetto VSIX per Visual Studio 2022 e versioni successive e un progetto VSIX per Visual Studio 2019 e versioni precedenti. Ognuno di questi progetti contiene solo un e il pacchetto fa riferimento `source.extension.vsixmanifest` all'SDK 16.x o all'SDK 17.x. Questi progetti VSIX avrebbero anche un riferimento di progetto condiviso a un nuovo progetto condiviso che ospiterà tutto il codice sorgente che può essere condiviso tra le due versioni di Visual Studio.

Come punto di partenza, per questo documento si presuppone che sia già presente un progetto VSIX destinato a Visual Studio 2019 e che l'estensione funzioni su Visual Studio 2022.

Tutti questi passaggi possono essere completati con Visual Studio 2019.

1. Se non è già stato fatto, [modernizzare i progetti](#modernize-your-vsix-project) per semplificare i passaggi più avanti in questo processo di aggiornamento.

1. Aggiungere un nuovo progetto condiviso alla soluzione per ogni progetto esistente che fa riferimento a VS SDK.
   ![Comando Aggiungi nuovo progetto ](media/update-visual-studio-extension/add-new-project.png)
    ![ Nuovo modello di progetto](media/update-visual-studio-extension/new-shared-project-template.png)

1. Aggiungere un riferimento da ogni progetto di riferimento di VS SDK alla controparte del progetto condiviso.
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Aggiungere informazioni di riferimento sul progetto condiviso" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Spostare tutto il codice sorgente (inclusi .cs, .resx) da ogni progetto di riferimento di VS SDK alla controparte del progetto condiviso.
Lasciare il `source.extension.vsixmanifest` file nel progetto VSIX.
   ![Il progetto condiviso contiene tutti i file di origine](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. I file di metadati (note sulla versione, licenza, icone e così via) e i file VSCT devono essere spostati in una directory condivisa e aggiunti come file collegati al progetto VSIX.
   ![Aggiungere metadati e file VSCT come file collegati](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - Per i file di metadati, impostare BuildAction su `Content` e impostare Includi in VSIX su `true` .

      ![Includere file di metadati in VSIX](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - Per i file VSCT, impostare BuildAction su `VSCTCompile` e non includere in VSIX.
      Visual Studio possibile che questa impostazione non sia supportata, ma è possibile modificare manualmente l'azione di compilazione scaricando il progetto e `Content` impostandola su `VSCTCompile`

    ```diff
    -<Content Include="..\SharedFiles\VSIXProject1Package.vsct">
    -  <Link>VSIXProject1Package.vsct</Link>
    -</Content>
    +<VSCTCompile Include="..\SharedFiles\VSIXProject1Package.vsct">
    +  <Link>VSIXProject1Package.vsct</Link>
    +  <ResourceName>Menus.ctmenu</ResourceName>
    +</VSCTCompile>
    ```

      ![Impostare i file VSCT come VSCTCompile](media/update-visual-studio-extension/build-linked-vsct-files.png)

1. Compilare i progetti per verificare di non aver introdotto nuovi errori.

Il progetto è ora pronto per aggiungere il Visual Studio 2022.

## <a name="add-a-visual-studio-2022-target"></a>Aggiungere una destinazione Visual Studio 2022

Questo documento presuppone che siano stati completati i passaggi per eseguire [il factor Visual Studio'estensione con progetti condivisi.](#use-shared-projects-for-multi-targeting)

Continuare ad aggiungere Visual Studio 2022 all'estensione con questi passaggi, che possono essere completati usando Visual Studio 2019:

1. Aggiungere un nuovo progetto VSIX alla soluzione. Si tratta del progetto destinato a Visual Studio 2022. Rimuovere il codice sorgente fornito con il modello, ma *mantenere il `source.extension.vsixmanifest` file*.

1. Nel nuovo progetto VSIX aggiungere un riferimento al progetto condiviso allo stesso progetto condiviso a cui fa riferimento Visual Studio VSIX con destinazione 2019.

   ![Una soluzione con un progetto condiviso e due progetti VSIX](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Verificare che il nuovo progetto VSIX venga compilato correttamente. Potrebbe essere necessario aggiungere riferimenti in modo che corrispondano al progetto VSIX originale per risolvere eventuali errori del compilatore.

1. Per le estensioni vs gestite, aggiornare i riferimenti al pacchetto dalla versione 16.x (o precedente) alle versioni del pacchetto 17.x nel file di progetto di destinazione di Visual Studio 2022 usando il Gestione pacchetti NuGet o modificando direttamente il file di progetto:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Si useranno versioni effettivamente disponibili da nuget.org. Quelli usati in precedenza sono solo a scopo dimostrativo.

   In molti casi, gli ID pacchetto sono stati modificati. Per un elenco [delle modifiche](migrated-assemblies.md) apportate in Visual Studio 2022, vedere la tabella di mapping di pacchetti/assembly.

   Le estensioni scritte in C++ non hanno ancora un SDK disponibile con cui eseguire la compilazione.

1. Per i progetti C++, devono essere compilati per amd64. Per le estensioni gestite, valutare la possibilità di modificare il progetto dalla compilazione per Qualsiasi CPU alla destinazione , per riflettere che in Visual Studio 2022 l'estensione viene sempre caricata in un processo `x64` a 64 bit. `Any CPU` è anche valido, ma può generare avvisi se si fa riferimento a file binari nativi solo x64.

   Qualsiasi dipendenza che l'estensione può avere in un modulo nativo dovrà essere aggiornata da un'immagine x86 a un'immagine amd64.

1. Modificare il `source.extension.vsixmanifest` file per riflettere la destinazione Visual Studio 2022. Impostare il `<InstallationTarget>` tag in modo che rifletta Visual Studio 2022 e indicare un payload amd64:

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   In Visual Studio 2019, la finestra di progettazione per questo file non espone il nuovo elemento, quindi questa modifica dovrà essere eseguita con un editor XML, a cui è possibile accedere tramite il comando Apri `ProductArchitecture` **con in Esplora soluzioni**. 

   Questo `ProductArchitecture` elemento è critico. Visual Studio 2022 non *installerà* l'estensione senza di essa.

   | Elemento | valore | Descrizione |
   | - | - | - |
   | ProductArchitecture | X86, AMD64 | Piattaforme supportate da questo VSIX. Senza distinzione tra maiuscole e minuscole. Una piattaforma per ogni elemento e un elemento per InstallTarget. Per le versioni del prodotto inferiori alla 17.0 il valore predefinito è x86 e può essere omesso.  Per le versioni del prodotto 17.0 e successive questo elemento è obbligatorio e non esiste alcun valore predefinito. Ad Visual Studio 2022 l'unico contenuto valido per questo elemento è "amd64". |

1. Apportare eventuali altre modifiche necessarie in source.extension.vsixmanifest in modo che corrisponda a quella destinata a Visual Studio 2019 (se presente). È fondamentale che l'ID di VSIX, nell'elemento del manifesto, sia `Identity` identico per entrambe le estensioni.

A questo punto, è presente un'estensione Visual Studio 2022 di destinazione VSIX. È consigliabile compilare Visual Studio progetto VSIX di destinazione 2022 e usare tutte le [interruzioni di compilazione visualizzate.](#handle-breaking-api-changes) Se non sono presenti interruzioni di compilazione nel progetto VSIX di destinazione Visual Studio 2022, si è pronti per il test.

## <a name="handle-breaking-api-changes"></a>Gestire le modifiche dell'API di rilievo

Sono presenti [modifiche dell'API](breaking-api-list.md) di rilievo Visual Studio 2022 che potrebbero richiedere modifiche al codice da quando è stato eseguito in versioni precedenti. Esaminare questo documento per suggerimenti su come aggiornare il codice per ognuno di essi.

Quando si adatta il codice, [](#use-conditional-compilation-symbols) è consigliabile usare la compilazione condizionale in modo che il codice possa continuare a supportare il pre-Visual Studio 2022 aggiungendo il supporto per Visual Studio 2022.

Quando si ottiene l'Visual Studio di estensione destinata alla versione 2022, procedere al [test di](#test-your-extension).

## <a name="use-conditional-compilation-symbols"></a>Usare simboli di compilazione condizionale

Se si vuole usare lo stesso codice sorgente, anche lo stesso file, per Visual Studio 2022 e versioni precedenti, potrebbe essere necessario usare la compilazione condizionale in modo da poter creare un fork del codice per adattarsi alle modifiche di rilievo. La compilazione condizionale è una funzionalità dei linguaggi C#, Visual Basic e C++ che può essere usata per condividere la maggior parte del codice, mantenendo al tempo stesso le API divergenti in posizioni specifiche.

Altre informazioni sull'uso delle direttive del preprocessore e dei simboli di compilazione condizionale sono disponibili nella documentazione Microsoft #if [direttiva per il preprocessore](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation).

I progetti che hanno come destinazione versioni precedenti Visual Studio dovranno usare un simbolo di compilazione condizionale che può quindi essere usato per creare un fork del codice per usare le diverse API. È possibile impostare il simbolo di compilazione condizionale nella pagina delle proprietà del progetto, come illustrato nell'immagine seguente:

![Impostazione dei simboli di compilazione condizionale](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Assicurarsi di impostare il simbolo di compilazione per *tutte le* configurazioni, perché per impostazione predefinita il simbolo immesso può essere applicato solo a una configurazione.

### <a name="c-techniques"></a>Tecniche \# C

È quindi possibile usare tale simbolo come direttiva di preprocessore ( `#if` ) come illustrato nel codice seguente. È quindi possibile creare un fork del codice per gestire la modifica di rilievo tra le diverse Visual Studio versioni.

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
#if Visual Studio 2019
    shell.LoadUILibrary(myGuid, myFlags, out uint ptrLib);
#else
    shell.LoadUILibrary(myGuid, myFlags, out IntPtr ptrLib);
#endif
```

In alcuni casi, è sufficiente usare per evitare di assegnare un nome al tipo, evitando così `var` la necessità di `#if` aree. Il frammento di codice precedente può anche essere scritto come:

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

Quando si usa la sintassi, si noti come è possibile usare l'elenco Visual Studio discesa del contesto del servizio di linguaggio nel documento illustrato di seguito per modificare l'evidenziazione della sintassi e l'altro per aiutare il servizio di linguaggio a concentrare l'attenzione su una versione di Visual Studio di destinazione per l'estensione `#if` e un'altra.

![Compilazione condizionale in un progetto condiviso](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>Tecniche di condivisione XAML

XAML non ha alcun preprocessore per consentire la personalizzazione del contenuto in base ai simboli del preprocessore. Potrebbe essere necessario copiare e gestire due pagine XAML in cui il contenuto deve essere diverso Visual Studio 2022 e versioni precedenti.

Tuttavia, in alcuni casi, un riferimento a un tipo presente in assembly distinti tra Visual Studio 2022 e versioni precedenti potrebbe comunque essere rappresentabile in un file XAML rimuovendo lo spazio dei nomi che fa riferimento all'assembly:

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>Testare l'estensione

Per testare un'estensione destinata Visual Studio 2022, è necessario avere installato Visual Studio 2022 Preview.
Non sarà possibile eseguire estensioni a 64 bit nelle versioni di Visual Studio precedenti Visual Studio 2022 Preview.

È possibile usare Visual Studio 2022 Preview per compilare e testare le estensioni indipendentemente dal fatto che siano Visual Studio 2022 o una versione precedente. Quando si avvia un progetto VSIX da Visual Studio 2022 verrà avviata un'istanza sperimentale di Visual Studio.

È consigliabile testare con ogni versione di Visual Studio che si intende supportare l'estensione.

A questo punto è possibile [pubblicare l'estensione](#publish-your-extension).

## <a name="publish-your-extension"></a>Pubblicare l'estensione

È stata quindi aggiunta una destinazione Visual Studio 2022 all'estensione e ne è stato testato il test. A questo punto è possibile pubblicare l'estensione per il mondo.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

La pubblicazione dell'estensione [nel Visual Studio Marketplace](https://marketplace.visualstudio.com/) è un ottimo modo per consentire ai nuovi utenti di trovare e installare l'estensione. Sia che l'estensione Visual Studio 2022 sia destinata esclusivamente a versioni precedenti di Visual Studio, Marketplace è disponibile per supportare l'utente.

In futuro, Marketplace consentirà di caricare più VSIX in un'unica inserzione del Marketplace, consentendo di caricare il pacchetto VSIX di destinazione Visual Studio 2022 e un vsix pre-Visual Studio 2022. Gli utenti otterrà automaticamente il vsix giusto per la versione di Visual Studio installata, quando usano Gestione estensioni di Visual Studio.

Per le versioni di anteprima di Visual Studio 2022, marketplace supporterà solo un singolo file VSIX per ogni inserzione del Marketplace. Mentre Visual Studio 2022 è in anteprima, è necessario avere un'inserzione separata Visual Studio Marketplace 2022 per l'estensione. In questo modo è possibile scorrere l'Visual Studio 2022 in base alle esigenze senza influire sui clienti sulle versioni precedenti di Visual Studio. È anche possibile contrassegnare l'estensione come "anteprima" per impostare l'aspettativa che sarà probabilmente meno affidabile, anche se l'origine di tale inaffiabilità è Visual Studio 2022, rispetto all'estensione mainstream.

### <a name="custom-installer"></a>Programma di installazione personalizzato

Se si compila un file MSI/EXE per installare l'estensione e si genera vsixinstaller.exe per installare (parte dell'estensione), verificare che il programma di installazione VSIX in Visual Studio 2022 sia stato aggiornato. Gli sviluppatori dovranno usare la versione del programma di installazione VSIX fornita con Visual Studio 2022 per installare le estensioni per Visual Studio 2022. Il programma di installazione VSIX in Visual Studio 2022 installerà anche le estensioni applicabili che hanno come destinazione le versioni precedenti di Visual Studio installate affiancate a Visual Studio 2022 nello stesso computer.

### <a name="network-share"></a>Condivisione di rete

È possibile condividere l'estensione su una LAN o in qualsiasi altro modo. Se si ha come destinazione Visual Studio 2022 e pre-Visual Studio 2022, sarà necessario condividere più VSIX singolarmente e assegnare loro nomi file (o posizionarli in cartelle univoche) che consentono agli utenti di sapere quale VSIX installare in base alla versione di Visual Studio installata.

### <a name="other-considerations"></a>Altre considerazioni

#### <a name="dependencies"></a>Dipendenze

Se VSIX specifica un altro VSIX come dipendenza tramite l'elemento , ogni vsix di riferimento deve essere installato nelle stesse destinazioni e nelle architetture di prodotto di `<dependency>` VSIX. Se un vsix dipendente non supporta l'installazione di destinazione di Visual Studio, l'installazione di VSIX avrà esito negativo. È possibile che il vsix dipendente supporti più destinazioni e architetture rispetto alla propria, ma non meno. Questa restrizione significa che l'approccio di distribuzione e distribuzione di un VSIX con dipendenze deve rispecchiare quello dei dipendenti.

## <a name="q--a"></a>Domande e risposte

**D:** L'estensione non richiede modifiche di interoperabilità perché fornisce solo dati (ad esempio, modelli), è possibile creare una singola estensione che includa anche Visual Studio 2022?

**A**: Sì!  Per [altre informazioni, vedere](#extensions-without-running-code) Estensioni senza eseguire codice.

**D:** Una dipendenza NuGet sta generando assembly di interoperabilità vecchi e causando classi in conflitto.

**:** aggiungere la riga seguente al file con estensione csproj per evitare assembly duplicati:

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

In questo modo si impedisce ai riferimenti al pacchetto di importare la versione precedente dell'assembly da altre dipendenze.

**D:** I comandi e i tasti di scelta rapida non funzionano in Visual Studio dopo il passaggio dei file di origine a un progetto condiviso.

**A:** [Il passaggio 2.4 dell'esempio](samples.md#step-2---refactor-source-code-into-a-shared-project) di Image Optimizer illustra come aggiungere file VSCT come elementi collegati in modo che siano compilati nel file VSCT.

## <a name="next-steps"></a>Passaggi successivi

Seguire un esempio di procedura dettagliata, [ImageOptimizer](samples.md), con collegamenti al progetto e alle modifiche al codice per ogni passaggio.
