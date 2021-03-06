---
title: Attività MT | Microsoft Docs
description: Informazioni sui parametri e sulle opzioni della riga di comando dell'attività MSBuild MT, che esegue il wrapping dello strumento Manifesto Microsoft mt.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
- MSBUILD (C++), MT task
- MT task (MSBuild (C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a023c58e528b2cda74fa42fcce46fd9c39059459
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905438"
---
# <a name="mt-task"></a>attività MT

Esegue il wrapping dello strumento Manifesto Microsoft, *mt.exe*. Per altre informazioni, vedere [Mt.exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività **MT**. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.

> [!NOTE]
> Nella documentazione *mt.exe* viene utilizzato un trattino ( **-** ) come prefisso per le opzioni della riga di comando, ma in questo argomento viene utilizzata una barra ( **/** ). Entrambi i prefissi sono accettabili.

|Parametro|Descrizione|
|---------------|-----------------|
|**AdditionalManifestFiles**|Parametro **String []** facoltativo.<br /><br /> Specifica il nome di uno o più file manifesto.<br /><br /> Per altre informazioni, vedere l'opzione **/manifest** in [Mt.exe](/windows/desktop/SbsCs/mt-exe) sul sito Web.|
|**AdditionalOptions**|Parametro **stringa** facoltativo.<br /><br /> Elenco di opzioni della riga di comando. Ad esempio,/ \<option1>  / \<option2>  / \<option#> . Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività **MT**.<br /><br /> Per altre informazioni, vedere [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AssemblyIdentity**|Parametro **stringa** facoltativo.<br /><br /> Specifica i valori dell'attributo dell'elemento **assemblyIdentity** del manifesto. Specificare un elenco delimitato da virgole, in cui il primo componente è il valore dell' `name` attributo, seguito da una o più coppie nome/valore con formato, *\<attribute name> =<ATTRIBUTE_VALUE>*.<br /><br /> Per altre informazioni, vedere l'opzione **/identity** in [Mt.exe](/windows/desktop/SbsCs/mt-exe) sul sito Web.|
|**ComponentFileName**|Parametro **stringa** facoltativo.<br /><br /> Specifica il nome della libreria di collegamento dinamico che si intende compilare dai file con estensione *rgs* o *tlb*. Questo parametro è obbligatorio se si specifica il parametro **RegistrarScriptFile** o **TypeLibraryFile** dell'attività MT.<br /><br /> Per altre informazioni, vedere l'opzione **/dll** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**DependencyInformationFile**|Parametro **stringa** facoltativo.<br /><br /> Specifica il file di informazioni sulle dipendenze usato da Visual Studio per tenere traccia delle informazioni sulle dipendenze della compilazione per lo strumento Manifesto.|
|**EmbedManifest**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, incorpora il file manifesto nell'assembly. Se `false`, crea un file manifesto autonomo.|
|**EnableDPIAwareness**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, aggiunge al manifesto informazioni che contrassegnano l'applicazione come compatibile con DPI. Scrivere un'applicazione compatibile con DPI consente di mantenere corretto e coerente l'aspetto di un'interfaccia utente usando un'ampia gamma di impostazioni di visualizzazione ad alta risoluzione.<br /><br /> Per altre informazioni, vedere [High DPI](/windows/desktop/win7devguide/high-dpi) (Risoluzione elevata).|
|**GenerateCatalogFiles**|Parametro `Boolean` facoltativo.<br /><br /> Se `true` , genera file di definizione del catalogo (con *estensione CDF*).<br /><br /> Per altre informazioni, vedere l'opzione **/makecdfs** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**GenerateCategoryTags**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, consente la generazione di tag di categoria. Se questo parametro è `true`, è necessario specificare anche il parametro **ManifestFromManagedAssemblyMT** dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/category** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**InputResourceManifests**|Parametro **stringa** facoltativo.<br /><br /> Esegue l'input del manifesto da una risorsa di tipo RT_MANIFEST con l'ID specificato. Specificare una risorsa nel formato \<file> [; [ #] \<resource_id> ], dove il \<resource_id> parametro facoltativo è un numero non negativo a 16 bit.<br /><br /> Se non viene specificato alcun valore `resource_id`, viene usato il valore predefinito CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Per altre informazioni, vedere l'opzione **/inputresource** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestFromManagedAssembly**|Parametro **stringa** facoltativo.<br /><br /> Genera un manifesto dall'assembly gestito specificato.<br /><br /> Per altre informazioni, vedere l'opzione **/managedassemblyname** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestToIgnore**|Parametro **stringa** facoltativo.<br /><br /> Non usato.|
|**OutputManifestFile**|Parametro **stringa** facoltativo.<br /><br /> Specifica il nome del manifesto di output. Se questo parametro viene omesso e si sta usando solo un manifesto, viene modificato quel manifesto.<br /><br /> Per altre informazioni, vedere l'opzione **/out** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**OutputResourceManifests**|Parametro **stringa** facoltativo.<br /><br /> Esegue l'output del manifesto in una risorsa di tipo RT_MANIFEST con l'ID specificato. Il formato della risorsa è \<file> [; [ #] \<resource_id> ], dove il \<resource_id> parametro facoltativo è un numero non negativo a 16 bit.<br /><br /> Se non viene specificato alcun valore `resource_id`, viene usato il valore predefinito CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Per altre informazioni, vedere l'opzione **/outputresource** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**RegistrarScriptFile**|Parametro **stringa** facoltativo.<br /><br /> Specifica il nome del file dello script di registrazione (con *estensione rgs*) da usare per il supporto del manifesto com senza registrazione.<br /><br /> Per altre informazioni, vedere l'opzione **/rgs** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ReplacementsFile**|Parametro **stringa** facoltativo.<br /><br /> Specifica il file che contiene i valori per le stringhe sostituibili nel file dello script di registrazione (con *estensione rgs*).<br /><br /> Per altre informazioni, vedere l'opzione **/replacements** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ResourceOutputFileName**|Parametro **stringa** facoltativo.<br /><br /> Specifica il file di risorse di output usato per incorporare il manifesto nell'output del progetto.|
|**recenti**|Parametro `ITaskItem[]` facoltativo.<br /><br /> Specifica un elenco di file di origine del manifesto separati da spazi.<br /><br /> Per altre informazioni, vedere l'opzione **/manifest** in [Mt.exe](/windows/desktop/SbsCs/mt-exe) sul sito Web.|
|**SuppressDependencyElement**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, genera un manifesto senza elementi di dipendenza. Se questo parametro è `true`, specificare anche il parametro **ManifestFromManagedAssemblyMT** dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/nodependency** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressStartupBanner**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/nologo** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**TrackerLogDirectory**|Parametro `String` facoltativo.<br /><br /> Specifica la directory intermedia in cui sono archiviati i log di rilevamento per questa attività.|
|**TypeLibraryFile**|Parametro **stringa** facoltativo.<br /><br /> Specifica il nome del file della libreria dei tipi (con *estensione TLB*). Se si specifica questo parametro, specificare anche il parametro **ComponentFileNameMT** dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/tlb** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**UpdateFileHashes**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, calcola il valore hash dei file nel percorso specificato dal parametro **UpdateFileHashesSearchPathMT** dell'attività e quindi aggiorna il valore dell'attributo **hash** dell'elemento **file** del manifesto usando il valore calcolato.<br /><br /> Per altre informazioni, vedere l'opzione **/hashupdate** in [Mt.exe](/windows/desktop/SbsCs/mt-exe). Vedere anche il parametro **UpdateFileHashesSearchPath** in questa tabella.|
|**UpdateFileHashesSearchPath**|Parametro `String` facoltativo.<br /><br /> Specifica il percorso di ricerca da usare quando si aggiornano gli hash dei file. Usare questo parametro con il parametro **UpdateFileHashesMT** dell'attività.<br /><br /> Per altre informazioni, vedere il parametro **UpdateFileHashes** in questa tabella.|
|**VerboseOutput**|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, visualizza informazioni dettagliate sul debug.<br /><br /> Per altre informazioni, vedere l'opzione **/verbose** in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
