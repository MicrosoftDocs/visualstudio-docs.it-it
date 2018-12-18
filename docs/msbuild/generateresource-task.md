---
title: "Attività GenerateResource | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 37aacbfd2095cf4edae78393569702fe4fea6c7e
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="generateresource-task"></a>Attività GenerateResource
Converte file con estensione txt o resx (formato di risorsa basato su XML) in file binari di Common Language Runtime (con estensione resources) che è possibile incorporare in un eseguibile binario di runtime o compilare in assembly satellite. In genere, questa attività viene usata per convertire file con estensione txt o resx in file con estensione resource. Dal punto di vista funzionale, l'attività `GenerateResource` è simile a [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `GenerateResource` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AdditionalInputs`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene input aggiuntivi per il controllo delle dipendenze eseguito da questa attività. Ad esempio, è in genere opportuno inserire come input i file di progetto e di destinazione, in modo da consentire la rigenerazione di tutte le risorse in caso di aggiornamento.|  
|`EnvironmentVariables`|Parametro `String[]` facoltativo.<br /><br /> Specifica una matrice di coppie nome/valore di variabili di ambiente che devono essere passate al file resgen.exe generato, oltre al normale blocco di ambiente (o all'esecuzione selettiva dell'override).|  
|`ExcludedInputPaths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica una matrice di elementi che indicano i percorsi dai quali gli input tracciati verranno ignorati durante la verifica dell'aggiornamento.|  
|`ExecuteAsTool`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, esegue i file tlbimp.exe e aximp.exe dal framework di destinazione appropriato in modalità out-of-process per generare gli assembly wrapper necessari. Questo parametro consente il multitargeting di `ResolveComReferences`.|  
|`FilesWritten`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene i nomi di tutti i file scritti nel disco, incluso, se presente, il file di cache. Questo parametro è particolarmente utile per le implementazioni di Clean.|  
|`MinimalRebuildFromTracking`|Parametro `Boolean` facoltativo.<br /><br /> Ottiene o imposta un'opzione che specifica se verrà usata la compilazione incrementale tracciata. Se `true`, viene attivata la compilazione incrementale. In caso contrario, verrà forzata una ricompilazione.|  
|`NeverLockTypeAssemblies`|Parametro `Boolean` facoltativo.<br /><br /> Ottiene o imposta un valore booleano che specifica se creare un nuovo oggetto [AppDomain](/dotnet/api/system.appdomain) per valutare i file di risorse (RESX) (true) o se creare un nuovo oggetto [AppDomain](/dotnet/api/system.appdomain) solo quando i file di risorse fanno riferimento a un assembly dell'utente (false).|  
|`OutputResources`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica il nome dei file generati, inclusi i file con estensione resources. Se non si specifica un nome, viene usato il nome del file di input corrispondente e il file con estensione resources creato viene inserito nella directory contenente il file di input.|  
|`PublicClass`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, crea una classe di risorse fortemente tipizzata come classe pubblica.|  
|`References`|Parametro `String[]` facoltativo.<br /><br /> Specifica i riferimenti per il caricamento dei tipi nei file con estensione resx. Gli elementi dati dei file resx possono essere di tipo .NET. Se il file resx viene letto, deve essere risolto. In genere, è possibile risolverlo correttamente usando le regole di caricamento dei tipi standard. Hanno la precedenza eventuali assembly specificati in `References`.<br /><br /> Questo parametro non è obbligatorio per le risorse fortemente tipizzate.|  
|`SdkToolsPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso degli strumenti SDK, ad esempio resgen.exe.|  
|`Sources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica gli elementi da convertire. Gli elementi passati a questo parametro devono avere una delle estensioni di file seguenti:<br /><br /> -   `.txt`: specifica l'estensione di un file di testo da convertire. I file di testo possono contenere solo risorse di tipo stringa.<br />-   `.resx`: specifica l'estensione di un file di risorse basato su XML da convertire.<br />-   `.restext`: specifica lo stesso formato dell'estensione txt. Questa diversa estensione consente di distinguere chiaramente i file di origine che contengono risorse dagli altri file di origine nel processo di compilazione.<br />-   `.resources`: specifica l'estensione di un file di risorse da convertire.|  
|`StateFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il percorso di un file di cache facoltativo usato per accelerare il controllo delle dipendenze dei collegamenti nei file di input resx.|  
|`StronglyTypedClassName`|Parametro `String` facoltativo.<br /><br /> Specifica il nome della classe di risorse fortemente tipizzata. Se questo parametro non è specificato, viene usato il nome base del file di risorse.|  
|`StronglyTypedFilename`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del file di origine. Se questo parametro non è specificato, viene usato il nome della classe come nome base e l'estensione viene determinata dal linguaggio. Ad esempio: `MyClass.cs`.|  
|`StronglyTypedLanguage`|Parametro `String` facoltativo.<br /><br /> Specifica il linguaggio da usare per generare l'origine della classe per la risorsa fortemente tipizzata. Questo parametro deve corrispondere esattamente a uno dei linguaggi usati da CodeDomProvider. Ad esempio: `VB` o `C#`.<br /><br /> Il passaggio di un valore a questo parametro determina la generazione di risorse fortemente tipizzate.|  
|`StronglyTypedManifestPrefix`|Parametro `String` facoltativo.<br /><br /> Specifica lo spazio dei nomi della risorsa o il prefisso del manifesto da usare nell'origine della classe generata per la risorsa fortemente tipizzata.|  
|`StronglyTypedNamespace`|Parametro `String` facoltativo.<br /><br /> Specifica lo spazio dei nomi da usare per l'origine della classe generata per la risorsa fortemente tipizzata. Se questo parametro non è specificato, tutte le risorse fortemente tipizzate vengono incluse nello spazio dei nomi globale.|  
|`TLogReadFiles`|Parametro di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene una matrice di elementi che rappresentano i log di rilevamento delle operazioni di lettura.|  
|`TLogWriteFiles`|Parametro di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene una matrice di elementi che rappresentano i log di rilevamento delle operazioni di scrittura.|  
|`ToolArchitecture`|Parametro <xref:System.String?displayProperty=fullName> facoltativo.<br /><br /> Consente di determinare se per la generazione di ResGen.exe è necessario o meno usare Tracker.exe.<br /><br /> Deve essere analizzabile rispetto a un membro dell'enumerazione <xref:Microsoft.Build.Utilities.ExecutableType>. Se `String.Empty`, viene usata un'euristica per determinare un'architettura predefinita. Deve essere analizzabile rispetto a un membro dell'enumerazione Microsoft.Build.Utilities.ExecutableType.|  
|`TrackerFrameworkPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso della posizione appropriata di .NET Framework in cui è contenuto il file FileTracker.dll.<br /><br /> Se questo parametro è impostato, l'utente si assume la responsabilità di assicurarsi che il numero di bit del file FileTracker.dll passato corrisponda al numero di bit del file ResGen.exe che intende usare. In caso contrario, la posizione appropriata viene stabilita dall'attività in base alla versione corrente di .NET Framework.|  
|`TrackerLogDirectory`|Parametro `String` facoltativo.<br /><br /> Specifica la directory intermedia in cui verranno inseriti i log di rilevamento risultanti dall'esecuzione di questa attività.|  
|`TrackerSdkPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso della posizione appropriata di Windows SDK in cui è contenuto il file Tracker.exe.<br /><br /> Se questo parametro è impostato, l'utente si assume la responsabilità di assicurarsi che il numero di bit del file Tracker.exe passato corrisponda al numero di bit del file ResGen.exe che intende usare. In caso contrario, la posizione appropriata viene stabilita dall'attività in base alla versione corrente di Windows SDK.|  
|`TrackFileAccess`|Parametro <xref:System.Boolean> facoltativo.<br /><br /> Se true, la directory del file di input viene usata per risolvere i percorsi di file relativi.|  
|`UseSourcePath`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica che è necessario usare la directory del file di input per risolvere i percorsi di file relativi.|  
  
## <a name="remarks"></a>Note  
 Poiché i file con estensione resx possono contenere collegamenti ad altri file di risorse, non è sufficiente confrontare i timestamp dei file resx e resources per verificare che gli output siano aggiornati. Per questo motivo, l'attività `GenerateResource` segue i collegamenti nei file resx e al tempo stesso controlla i timestamp dei file collegati. Ne consegue che, in genere, non è consigliabile usare gli attributi `Inputs` e `Outputs` nella destinazione che contiene l'attività `GenerateResource`. In questo modo, infatti, è possibile che l'attività venga ignorata anziché essere eseguita.  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
 Se si usa MSBuild 4.0 come destinazione di progetti .NET 3.5, è possibile che la compilazione sulle risorse x86 non riesca. Per risolvere questo problema, è possibile compilare la destinazione come assembly AnyCPU.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usata l'attività `GenerateResource` per generare file resources dai file specificati dalla raccolta di elementi `Resx`.  
  
```xml  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 L'attività `GenerateResource` usa il metadato \<LogicalName> di un elemento \<EmbeddedResource> per assegnare un nome alla risorsa incorporata in un assembly.  
  
 Supponendo che l'assembly si chiami myAssembly, il codice seguente genera una risorsa incorporata denominata someQualifier.someResource.resources:  
  
```xml  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Senza il metadato \<LogicalName>, la risorsa verrebbe denominata myAssembly.myResource.resources.  Questo esempio si applica solo a Visual Basic e al processo di compilazione di Visual C#.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
