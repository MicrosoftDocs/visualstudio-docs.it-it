---
title: "Attività AL (Assembly Linker) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d9d3b433e7ae14603a41b7ad802ff386c7aac52
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="al-assembly-linker-task"></a>Attività AL (Assembly Linker)
L'attività AL esegue il wrapping di AL.exe, uno strumento distribuito con [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Lo strumento Assembly Linker consente di creare un assembly con un manifesto da uno o più file che costituiscono moduli o file di risorse. Poiché è possibile che negli ambienti di compilazione e sviluppo queste funzionalità siano già disponibili, spesso non è necessario usare direttamente questa attività. Assembly Linker è particolarmente utile per gli sviluppatori che hanno la necessità di creare un unico assembly da più file di componenti, ad esempio quelli che possono essere prodotti dallo sviluppo in linguaggi misti. Questa attività non combina i moduli in un unico file assembly. Affinché l'assembly ottenuto venga caricato correttamente, è comunque necessario che i singoli moduli vengano distribuiti e che siano disponibili. Per altre informazioni su AL.exe, vedere [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `AL` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AlgorithmID`|Parametro `String` facoltativo.<br /><br /> Specifica un algoritmo per generare un hash per tutti i file di un assembly su più file, ad eccezione del file contenente il manifesto dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/algid` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`BaseAddress`|Parametro `String` facoltativo.<br /><br /> Specifica l'indirizzo in corrispondenza del quale caricare una DLL nel computer dell'utente in fase di esecuzione. Il caricamento delle applicazioni risulta più veloce se si specifica l'indirizzo di base delle DLL, anziché lasciare al sistema operativo il compito di rilocare le DLL nello spazio di processo. Questo parametro corrisponde all'opzione /base[address](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`CompanyName`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Company` dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/comp[any]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Configuration`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Configuration` dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/config[uration]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Copyright`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Copyright` dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/copy[right]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Culture`|Parametro `String` facoltativo.<br /><br /> Specifica la stringa di impostazioni cultura da associare all'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/c[ulture]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, nell'assembly viene inserita solo la chiave pubblica. Se è impostato su `false`, l'assembly viene firmato completamente. Per altre informazioni, vedere la documentazione relativa all'opzione `/delay[sign]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Description`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Description` dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/descr[iption]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`EmbedResources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Incorpora le risorse specificate nell'immagine contenente il manifesto dell'assembly. Questa attività copia nell'immagine il contenuto del file di risorse. È possibile che agli elementi passati a questo parametro siano associati metadati facoltativi denominati `LogicalName` e `Access`. Il metadato `LogicalName` viene usato per specificare l'identificatore interno per la risorsa,  mentre il metadato `Access` può essere impostato su `private` per rendere la risorsa invisibile ad altri assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/embed[resource]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`EvidenceFile`|Parametro `String` facoltativo.<br /><br /> Incorpora il file specificato nell'assembly con il nome di risorsa `Security.Evidence`.<br /><br /> Non è possibile usare il nome `Security.Evidence` per risorse regolari. Questo parametro corrisponde all'opzione `/e[vidence]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`ExitCode`|Parametro di sola lettura di output `Int32` facoltativo.<br /><br /> Specifica il codice di uscita fornito dal comando eseguito.|  
|`FileVersion`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `File Version` dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/fileversion` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Flags`|Parametro `String` facoltativo.<br /><br /> Specifica un valore per il campo `Flags` dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/flags` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`GenerateFullPaths`|Parametro `Boolean` facoltativo.<br /><br /> Impone l'uso del percorso assoluto per tutti i file segnalati in un messaggio di errore. Questo parametro corrisponde all'opzione `/fullpaths` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica un contenitore che include una coppia di chiavi. Tale parametro firmerà l'assembly, ossia assegnerà a quest'ultimo un nome sicuro, inserendo una chiave pubblica nel manifesto dell'assembly. L'attività firmerà quindi l'assembly finale con la chiave privata. Per altre informazioni, vedere la documentazione relativa all'opzione `/keyn[ame]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica un file contenente una coppia di chiavi o solo una chiave pubblica da usare per la firma di un assembly. Durante la compilazione la chiave pubblica verrà inserita nel manifesto dell'assembly, mentre l'assembly finale verrà firmato con la chiave privata. Per altre informazioni, vedere la documentazione relativa all'opzione `/keyf[ile]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`LinkResources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Collega i file di risorse specificati a un assembly. La risorsa specificata diventa parte dell'assembly, ma il file non viene copiato. È possibile che agli elementi passati a questo parametro siano associati metadati facoltativi denominati `LogicalName`, `Target` e `Access`. Il metadato `LogicalName` viene usato per specificare l'identificatore interno per la risorsa, mentre il metadato `Target` consente di specificare il percorso e il nome file in cui viene copiato il file prima che il nuovo file venga compilato nell'assembly. Il metadato `Access`, infine, può essere impostato su `private` per rendere la risorsa invisibile ad altri assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/link[resource]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`MainEntryPoint`|Parametro `String` facoltativo.<br /><br /> Specifica il nome completo (*classe.metodo*) del metodo da usare come punto di ingresso durante la conversione di un modulo in un file eseguibile. Questo parametro corrisponde all'opzione `/main` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`OutputAssembly`|Parametro di ouput <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del file generato dall'attività. Questo parametro corrisponde all'opzione `/out` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Limita le piattaforme su cui è possibile eseguire il codice. I valori possibili sono `x86`, `Itanium`, `x64` e `anycpu`. Il valore predefinito è `anycpu`. Questo parametro corrisponde all'opzione `/platform` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`ProductName`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Product` dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/prod[uct]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`ProductVersion`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `ProductVersion` dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/productv[ersion]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`ResponseFiles`|Parametro `String[]` facoltativo.<br /><br /> Specifica i file di risposta contenenti opzioni aggiuntive da passare ad Assembly Linker.|  
|`SdkToolsPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso degli strumenti SDK, ad esempio resgen.exe.|  
|`SourceModules`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Corrisponde a uno o più moduli da compilare in un assembly. I moduli verranno elencati nel manifesto dell'assembly ottenuto. Affinché l'assembly venga caricato, è comunque necessario che i moduli vengano distribuiti e che siano disponibili. È possibile che agli elementi passati a questo parametro siano associati metadati aggiuntivi denominati `Target`, in cui sono specificati il percorso e il nome file in cui viene copiato il file prima che il nuovo file venga compilato nell'assembly. Per altre informazioni, vedere la documentazione relativa ad [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). Questo parametro corrisponde all'elenco di moduli passati ad Al.exe senza usare un'opzione specifica.|  
|`TargetType`|Parametro `String` facoltativo.<br /><br /> Specifica il formato del file di output. I valori possibili sono: `library` per le librerie di codici, `exe` per le applicazioni console e `win` per le applicazioni basate su Windows. Il valore predefinito è `library`. Questo parametro corrisponde all'opzione `/t[arget]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`TemplateFile`|Parametro `String` facoltativo.<br /><br /> Specifica l'assembly dal quale ereditare tutti i metadati dell'assembly, ad eccezione del campo relativo alle impostazioni cultura. All'assembly specificato deve essere assegnato un nome sicuro.<br /><br /> Gli assembly creati con il parametro `TemplateFile` saranno assembly satellite. Questo parametro corrisponde all'opzione `/template` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Timeout`|Parametro `Int32` facoltativo.<br /><br /> Specifica la quantità di tempo, in millisecondi, dopo i quali l'eseguibile dell'attività viene terminato. Il valore predefinito è `Int.MaxValue`, con cui si indica che non esiste alcun periodo di timeout.|  
|`Title`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Title` dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/title` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`ToolPath`|Parametro `String` facoltativo.<br /><br /> Specifica la posizione da cui l'attività caricherà il file eseguibile sottostante (Al.exe). Se questo parametro non è specificato, viene usato il percorso di installazione SDK corrispondente alla versione del framework che esegue [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Trademark`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Trademark` dell'assembly. Per altre informazioni, vedere la documentazione relativa all'opzione `/trade[mark]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Version`|Parametro `String` facoltativo.<br /><br /> Specifica le informazioni sulla versione dell'assembly. Il formato della stringa è *principale.secondario.build.revisione*. Il valore predefinito è 0. Per altre informazioni, vedere la documentazione relativa all'opzione `/v[ersion]` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Win32Icon`|Parametro `String` facoltativo.<br /><br /> Inserisce nell'assembly un file icona (.ico). Il file .ico determina l'aspetto desiderato del file di output in Esplora File. Questo parametro corrisponde all'opzione `/win32icon` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
|`Win32Resource`|Parametro `String` facoltativo.<br /><br /> Inserisce nel file di output una risorsa Win32 (file .res). Per altre informazioni, vedere la documentazione relativa all'opzione `/win32res` di [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/tooltaskextension-base-class.md) (Classe di base TaskExtension).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato un assembly con le opzioni specificate.  
  
```xml  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  
  
    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  
  
    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)