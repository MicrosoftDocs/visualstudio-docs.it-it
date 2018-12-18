---
title: "Riferimenti delle attività MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1d3bd0cb011dd99183e3d7318693261e19e01791
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-task-reference"></a>Riferimenti delle attività MSBuild
Le attività forniscono il codice che viene eseguito durante il processo di compilazione. Le attività riportate nell'elenco seguente sono incluse in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Quando [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] è installato, sono disponibili attività aggiuntive usate per compilare progetti [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Per altre informazioni, vedere [Visual C++ Tasks](../msbuild/msbuild-tasks-specific-to-visual-cpp.md) (Attività Visual C++).  
  
 Oltre ai parametri elencati negli argomenti di questa sezione, ogni attività dispone anche dei parametri seguenti:  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Condition`|Parametro `String` facoltativo.<br /><br /> Espressione `Boolean` usata dal motore di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per determinare se l'attività verrà eseguita. Per altre informazioni sulle condizioni supportate da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], vedere [Condizioni](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parametro facoltativo. Può contenere uno dei valori seguenti:<br /><br /> -   **WarnAndContinue** o **true**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento [Target](../msbuild/target-element-msbuild.md) e della compilazione continua e tutti gli errori delle attività vengono considerati avvisi.<br />-   **ErrorAndContinue**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento `Target` e della compilazione continua e tutti gli errori delle attività vengono considerati errori.<br />-   **ErrorAndStop** o **false** (impostazione predefinita). Quando un'attività ha esito negativo, le attività rimanenti nell'elemento `Target` e la compilazione non vengono eseguite e l'intero elemento `Target` e la compilazione vengono considerati come non riusciti.<br /><br /> Le versioni di .NET Framework precedenti alla 4.5 supportano solo i valori `true` e `false`.<br /><br /> Per altre informazioni, vedere [Procedura: Ignorare gli errori nelle attività](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="in-this-section"></a>In questa sezione  
 [Classe di base Task](../msbuild/task-base-class.md)  
 Aggiunge diversi parametri alle attività che derivano dalla classe <xref:Microsoft.Build.Utilities.Task>.  
  
 [Classe di base TaskExtension](../msbuild/taskextension-base-class.md)  
 Aggiunge diversi parametri alle attività che derivano dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>.  
  
 [Classe di base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)  
 Aggiunge diversi parametri alle attività che derivano dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>.  
  
 [Attività AL (Assembly Linker)](../msbuild/al-assembly-linker-task.md)  
 Crea un assembly con un manifesto da uno o più file che costituiscono moduli o file di risorse.  
  
 [Attività AspNetCompiler](../msbuild/aspnetcompiler-task.md)  
 Esegue il wrapping di aspnet_compiler.exe, un'utilità per la precompilazione di applicazioni ASP.NET.  
  
 [Attività AssignCulture](../msbuild/assignculture-task.md)  
 Assegna gli identificatori delle impostazioni cultura agli elementi.  
  
 [Attività AssignProjectConfiguration](../msbuild/assignprojectconfiguration-task.md)  
 Accetta un elenco di stringhe di configurazione e li assegna ai progetti specificati.  
  
 [Attività AssignTargetPath](../msbuild/assigntargetpath-task.md)  
 Accetta un elenco di file e aggiunge gli attributi `<TargetPath>`, se non sono già specificati.  
  
 [Attività CallTarget](../msbuild/calltarget-task.md)  
 Richiama una destinazione nel file di progetto.  
  
 [Attività CombinePath](../msbuild/combinepath-task.md)  
 Combina i percorsi specificati in un singolo percorso.  
  
 [Attività ConvertToAbsolutePath](../msbuild/converttoabsolutepath-task.md)  
 Converte un percorso relativo, o un riferimento, in un percorso assoluto.  
  
 [Attività Copy](../msbuild/copy-task.md)  
 Copia i file in una nuova posizione.  
  
 [Attività CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md)  
 Crea un nome di manifesto di tipo [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] dal nome di un determinato file con estensione resx o da un'altra risorsa.  
  
 [Attività CreateItem](../msbuild/createitem-task.md)  
 Popola le raccolte di elementi dagli elementi di input, consentendo la copia degli elementi da un elenco a un altro.  
  
 [Attività CreateProperty](../msbuild/createproperty-task.md)  
 Popola le proprietà dai valori di input, consentendo la copia di tali valori da una proprietà o una stringa a un'altra.  
  
 [Attività CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Crea un nome di manifesto di tipo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] dal nome di un determinato file con estensione resx o da un'altra risorsa.  
  
 [Attività Csc](../msbuild/csc-task.md)  
 Richiama il compilatore Visual C# per creare librerie eseguibili a collegamento dinamico o moduli di codice.  
  
 [Attività Delete](../msbuild/delete-task.md)  
 Elimina i file specificati.  
  
 [Attività Error](../msbuild/error-task.md)  
 Interrompe una compilazione e registra un errore in base a un'istruzione condizionale valutata.  
  
 [Attività Exec](../msbuild/exec-task.md)  
 Esegue il programma o il comando specificato con gli argomenti specificati.  
  
 [Attività FindAppConfigFile](../msbuild/findappconfigfile-task.md)  
 Trova il file app.config, se presente, negli elenchi forniti.  
  
 [Attività FindInList](../msbuild/findinlist-task.md)  
 Trova un elemento in un elenco specificato con un itemspec corrispondente.  
  
 [Attività FindUnderPath](../msbuild/findunderpath-task.md)  
 Determina gli elementi di una raccolta specificata presenti nella cartella indicata e in tutte le relative sottocartelle.  
  
 [Attività FormatUrl task](../msbuild/formaturl-task.md)  
 Converte un URL in un formato URL corretto.  
  
 [Attività FormatVersion](../msbuild/formatversion-task.md)  
 Aggiunge il numero di revisione al numero di versione.  
  
 [Attività GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)  
 Genera un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o un manifesto nativo.  
  
 [Attività GenerateBootstrapper](../msbuild/generatebootstrapper-task.md)  
 Consente di rilevare, scaricare e installare automaticamente un'applicazione e i relativi prerequisiti.  
  
 [Attività GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)  
 Genera un manifesto di distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 [Attività GenerateResource](../msbuild/generateresource-task.md)  
 Converte i file con estensione txt e resx in file binari di Common Language Runtime con estensione resources.  
  
 [Attività GenerateTrustInfo](../msbuild/generatetrustinfo-task.md)  
 Genera l'attendibilità dell'applicazione dal manifesto di base e dai parametri `TargetZone` e `ExcludedPermissions`.  
  
 [Attività GetAssemblyIdentity](../msbuild/getassemblyidentity-task.md)  
 Recupera le identità degli assembly dai file specificati ed estrae le informazioni sulle identità.  
  
 [Attività GetFrameworkPath](../msbuild/getframeworkpath-task.md)  
 Recupera il percorso degli assembly [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Attività GetFrameworkSdkPath](../msbuild/getframeworksdkpath-task.md)  
 Recupera il percorso di [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
 [Attività GetReferenceAssemblyPaths](../msbuild/getreferenceassemblypaths-task.md)  
 Restituisce i percorsi degli assembly di riferimento dei vari framework.  
  
 [Attività LC](../msbuild/lc-task.md)  
 Genera un file con estensione license da un file con estensione licx.  
  
 [Attività MakeDir](../msbuild/makedir-task.md)  
 Crea directory e, se necessario, eventuali directory padre.  
  
 [Attività Message](../msbuild/message-task.md)  
 Registra un messaggio durante una compilazione.  
  
 [Attività Move](../msbuild/move-task.md)  
 Sposta i file in una nuova posizione.  
  
 [Attività MSBuild](../msbuild/msbuild-task.md)  
 Compila progetti di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] da un altro progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 [Attività ReadLinesFromFile](../msbuild/readlinesfromfile-task.md)  
 Legge un elenco di elementi da un file di testo.  
  
 [Attività RegisterAssembly](../msbuild/registerassembly-task.md)  
 Legge i metadati nell'assembly specificato e aggiunge le voci necessarie nel Registro di sistema.  
  
 [Attività RemoveDir](../msbuild/removedir-task.md)  
 Rimuove le directory specificate con tutti i relativi file e sottodirectory.  
  
 [Attività RemoveDuplicates](../msbuild/removeduplicates-task.md)  
 Rimuove gli elementi duplicati dalla raccolta di elementi specificata.  
  
 [Attività RequiresFramework35SP1Assembly](../msbuild/requiresframework35sp1assembly-task.md)  
 Determina se l'applicazione richiede .NET Framework 3.5 SP1.  
  
 Attività ResGen  
 Obsoleta. Usare l'[attività GenerateResource](../msbuild/generateresource-task.md) per convertire i file con estensione txt e resx in file binari di Common Language Runtime con estensione resources e viceversa.  
  
 [Attività ResolveAssemblyReference](../msbuild/resolveassemblyreference-task.md)  
 Determina tutti gli assembly che dipendono dall'assembly specificato.  
  
 [Attività ResolveComReference](../msbuild/resolvecomreference-task.md)  
 Accetta un elenco costituito da uno o più nomi di librerie dei tipi o file con estensione tlb e risolve tali librerie in percorsi sul disco.  
  
 [Attività ResolveKeySource](../msbuild/resolvekeysource-task.md)  
 Determina l'origine delle chiavi con nome sicuro.  
  
 [Attività ResolveManifestFiles](../msbuild/resolvemanifestfiles-task.md)  
 Risolve gli elementi seguenti del processo di compilazione nei file per la generazione del manifesto: elementi compilati, dipendenze, satelliti, contenuto, simboli di debug e documentazione.  
  
 [Attività ResolveNativeReference](../msbuild/resolvenativereference-task.md)  
 Risolve i riferimenti nativi.  
  
 [Attività ResolveNonMSBuildProjectOutput](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Determina i file di output per riferimenti a progetti non MSBuild.  
  
 [Attività SGen](../msbuild/sgen-task.md)  
 Crea un assembly di serializzazione XML per i tipi presenti nell'assembly specificato.  
  
 [Attività SignFile](../msbuild/signfile-task.md)  
 Consente di firmare il file specificato usando il certificato specificato.  
  
 [Attività Touch](../msbuild/touch-task.md)  
 Imposta l'ora di accesso e di modifica dei file.  
  
 [Attività UnregisterAssembly](../msbuild/unregisterassembly-task.md)  
 Annulla la registrazione degli assembly specificati ai fini dell'interoperabilità COM.  
  
 [Attività UpdateManifest](../msbuild/updatemanifest-task.md)  
 Aggiorna le proprietà selezionate in un manifesto e ripete la firma.  
  
 [Attività Vbc](../msbuild/vbc-task.md)  
 Richiama il compilatore Basic per creare librerie eseguibili a collegamento dinamico o moduli di codice.  
  
 [Attività Warning](../msbuild/warning-task.md)  
 Registra un avviso durante una compilazione in base a un'istruzione condizionale valutata.  
  
 [Attività WriteCodeFragment](../msbuild/writecodefragment-task.md)  
 Genera un file di codice temporaneo tramite il frammento di codice generato specificato. Non elimina il file.  
  
 [Attività WriteLinesToFile](../msbuild/writelinestofile-task.md)  
 Scrive gli elementi specificati nel file di testo indicato.  
  
 [Attività XmlPeek](../msbuild/xmlpeek-task.md)  
 Restituisce valori come specificato dalla query XPath da un file XML.  
  
 [XmlPoke Task](../msbuild/xmlpoke-task.md)  
 Imposta i valori come specificato da una query XPath in un file XML.  
  
 [Attività XslTransformation](../msbuild/xsltransformation-task.md)  
 Trasforma un input XML tramite *Extensible Stylesheet Language Transformation* (XSLT) o un XSLT compilato e gli output in un dispositivo o file di output.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Scrittura di attività](../msbuild/task-writing.md)   
 [Attività](../msbuild/msbuild-tasks.md)