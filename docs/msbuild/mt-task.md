---
title: Attività MT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (Visual C++), MT task
- MT task (MSBuild (Visual C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da1cc8b65ac43e05c692d1fe7a5af4d8ea6fe381
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="mt-task"></a>Attività MT
Esegue il wrapping dello strumento manifesto Microsoft, mt.exe. Per altre informazioni, vedere "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **MT**. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.  
  
> [!NOTE]
>  Nella documentazione di mt.exe viene usato un trattino (**-**) come prefisso per le opzioni della riga di comando, ma questo argomento usa una barra (**/**). Entrambi i prefissi sono accettabili.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Parametro **String[]** facoltativo.<br /><br /> Specifica il nome di uno o più file manifesto.<br /><br /> Per altre informazioni, vedere l'opzione **/manifest** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Elenco di opzioni della riga di comando. Ad esempio, "*/opzione1 /opzione2 /opzione#*". Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività **MT**.<br /><br /> Per altre informazioni, vedere "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**AssemblyIdentity**|Parametro **String** facoltativo.<br /><br /> Specifica i valori dell'attributo dell'elemento **assemblyIdentity** del manifesto. Specificare un elenco delimitato da virgole, dove il primo componente è il valore dell'attributo `name`, seguito da una o più coppie nome/valore nel formato *\<nome attributo> = <attributo_valore>*.<br /><br /> Per altre informazioni, vedere l'opzione **/identity** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ComponentFileName**|Parametro **String** facoltativo.<br /><br /> Specifica il nome della libreria di collegamento dinamico che si intende compilare dai file RGS o TLB. Questo parametro è obbligatorio se si specifica il parametro **RegistrarScriptFile** o **TypeLibraryFile** dell'attività MT.<br /><br /> Per altre informazioni, vedere l'opzione **/dll** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**DependencyInformationFile**|Parametro **String** facoltativo.<br /><br /> Specifica il file di informazioni sulle dipendenze usato da Visual Studio per tenere traccia delle informazioni sulle dipendenze della compilazione per lo strumento Manifesto.|  
|**EmbedManifest**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, incorpora il file manifesto nell'assembly. Se `false`, crea un file manifesto autonomo.|  
|**EnableDPIAwareness**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, aggiunge al manifesto informazioni che contrassegnano l'applicazione come compatibile con DPI. Scrivere un'applicazione compatibile con DPI consente di mantenere corretto e coerente l'aspetto di un'interfaccia utente usando un'ampia gamma di impostazioni di visualizzazione ad alta risoluzione.<br /><br /> Per altre informazioni, vedere "High DPI" (Risoluzione elevata) sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**GenerateCatalogFiles**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, genera i file di definizione del catalogo (CDF).<br /><br /> Per altre informazioni, vedere l'opzione **/makecdfs** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**GenerateCategoryTags**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, consente la generazione di tag di categoria. Se questo parametro è `true`, è necessario specificare anche il parametro **ManifestFromManagedAssemblyMT** dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/category** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**InputResourceManifests**|Parametro **String** facoltativo.<br /><br /> Esegue l'input del manifesto da una risorsa di tipo RT_MANIFEST con l'ID specificato. Specificare una risorsa nel formato *\<file>[***;***[***#***]<id_risorsa>]*, dove il parametro facoltativo `resource_id` è un numero non negativo a 16 bit.<br /><br /> Se non viene specificato alcun valore `resource_id`, viene usato il valore predefinito CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Per altre informazioni, vedere l'opzione **/inputresource** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ManifestFromManagedAssembly**|Parametro **String** facoltativo.<br /><br /> Genera un manifesto dall'assembly gestito specificato.<br /><br /> Per altre informazioni, vedere l'opzione **/managedassemblyname** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ManifestToIgnore**|Parametro **String** facoltativo.<br /><br /> Non usato.|  
|**OutputManifestFile**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del manifesto di output. Se questo parametro viene omesso e si sta usando solo un manifesto, viene modificato quel manifesto.<br /><br /> Per altre informazioni, vedere l'opzione **/out** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**OutputResourceManifests**|Parametro **String** facoltativo.<br /><br /> Esegue l'output del manifesto in una risorsa di tipo RT_MANIFEST con l'ID specificato. Il formato della risorsa è *\<file>[***;***[***#***]<id_risorsa>]*, dove il parametro facoltativo `resource_id` è un numero non negativo a 16 bit.<br /><br /> Se non viene specificato alcun valore `resource_id`, viene usato il valore predefinito CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Per altre informazioni, vedere l'opzione **/outputresource** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**RegistrarScriptFile**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del file di script di registrazione (RGS) da usare per il supporto al manifesto COM senza registrazione.<br /><br /> Per altre informazioni, vedere l'opzione **/rgs** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ReplacementsFile**|Parametro **String** facoltativo.<br /><br /> Specifica il file che contiene i valori per le stringhe sostituibili nel file di script di registrazione (RGS).<br /><br /> Per altre informazioni, vedere l'opzione **/replacements** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ResourceOutputFileName**|Parametro **String** facoltativo.<br /><br /> Specifica il file di risorse di output usato per incorporare il manifesto nell'output del progetto.|  
|**Sources**|Parametro `ITaskItem[]` facoltativo.<br /><br /> Specifica un elenco di file di origine del manifesto separati da spazi.<br /><br /> Per altre informazioni, vedere l'opzione **/manifest** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**SuppressDependencyElement**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, genera un manifesto senza elementi di dipendenza. Se questo parametro è `true`, specificare anche il parametro **ManifestFromManagedAssemblyMT** dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/nodependency** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**SuppressStartupBanner**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/nologo** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**TrackerLogDirectory**|Parametro `String` facoltativo.<br /><br /> Specifica la directory intermedia in cui sono archiviati i log di rilevamento per questa attività.|  
|**TypeLibraryFile**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del file di libreria dei tipi (TLB). Se si specifica questo parametro, specificare anche il parametro **ComponentFileNameMT** dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/tlb** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**UpdateFileHashes**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, calcola il valore hash dei file nel percorso specificato dal parametro **UpdateFileHashesSearchPathMT** dell'attività e quindi aggiorna il valore dell'attributo **hash** dell'elemento **file** del manifesto usando il valore calcolato.<br /><br /> Per altre informazioni, vedere l'opzione **/hashupdate** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737). Vedere anche il parametro **UpdateFileHashesSearchPath** in questa tabella.|  
|**UpdateFileHashesSearchPath**|Parametro `String` facoltativo.<br /><br /> Specifica il percorso di ricerca da usare quando si aggiornano gli hash dei file. Usare questo parametro con il parametro **UpdateFileHashesMT** dell'attività.<br /><br /> Per altre informazioni, vedere il parametro **UpdateFileHashes** in questa tabella.|  
|**VerboseOutput**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, visualizza informazioni dettagliate sul debug.<br /><br /> Per altre informazioni, vedere l'opzione **/verbose** in "Mt.exe" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)