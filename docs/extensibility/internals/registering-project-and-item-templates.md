---
title: Registrazione di Project and Item Templates | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c064a6632741eba69a553be87fb8f829063b266b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="registering-project-and-item-templates"></a>La registrazione di progetto e modelli di elemento
Tipi di progetto è necessario registrare le directory in cui si trovano i propri modelli di progetto e di elemento di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilizza le informazioni di registrazione associate con i tipi di progetto per determinare gli elementi da visualizzare nel **Aggiungi nuovo progetto** e **Aggiungi nuovo elemento** finestre di dialogo.  
  
 Per ulteriori informazioni sui modelli, vedere [aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Voci del Registro di sistema per i progetti  
 Gli esempi seguenti mostrano le voci del Registro di sistema in HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*versione*>. Le tabelle di accompagnamento descritti gli elementi utilizzati negli esempi.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|nome|Tipo|Descrizione|  
|----------|----------|-----------------|  
|@|REG_SZ|Nome predefinito di progetti di questo tipo.|  
|DisplayName|REG_SZ|ID di risorsa del nome da recuperare dalla DLL satellite registrato in pacchetti.|  
|Pacchetto|REG_SZ|ID di classe del pacchetto è stato registrato in pacchetti.|  
|ProjectTemplatesDir|REG_SZ|Percorso predefinito dei file di modello di progetto. I file di modello di progetto vengono visualizzati per il **nuovo progetto** modello.|  
  
### <a name="registering-item-templates"></a>Registrazione di modelli di elemento  
 È necessario registrare la directory in cui vengono archiviati i modelli di elemento.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|nome|Tipo|Descrizione|  
|----------|----------|-----------------|  
|@|REG_SZ|ID di risorsa per i modelli di Aggiungi elemento.|  
|TemplatesDir|REG_SZ|Percorso degli elementi di progetto visualizzati nella finestra di dialogo per la **Aggiungi nuovo elemento** procedura guidata.|  
|TemplatesLocalizedSubDir|REG_SZ|ID di risorsa di una stringa che assegna un nome di sottodirectory di TemplatesDir che contiene modelli localizzati. Poiché [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica la risorsa stringa dalla DLL satellite se sono stati, ogni DLL satellite può contenere un nome di sottodirectory della localizzata diversi.|  
|SortPriority|REG_DWORD|Impostare SortPriority per regolare l'ordine in cui i modelli vengono visualizzati nel **Aggiungi nuovo elemento** la finestra di dialogo. I valori maggiori di SortPriority vengono visualizzati in precedenza nell'elenco dei modelli.|  
  
### <a name="registering-file-filters"></a>Registrazione di filtri di file  
 Facoltativamente, è possibile registrare i filtri che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizza quando vengono richieste per nomi di file. Ad esempio, il [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtrare l'il **Apri File** è la finestra di dialogo:  
  
 **File Visual c# (\*. cs,\*. resx,\*Settings,\*XSD,\*WSDL);\*. cs,\*. resx,\*Settings,\*XSD,\*WSDL)**  
  
 Per supportare la registrazione di più filtri, ogni filtro è registrato nella propria sottochiave HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*versione*> \Projects\\{ \< *ProjectGUID*>} \Filters\\<*sottochiave*>. Il nome della sottochiave è arbitrario. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignora il nome della sottochiave e utilizza solo i valori.  
  
 È possibile controllare i contesti in cui viene utilizzato un filtro impostando flag, illustrato nella tabella seguente. Se un filtro non è impostato alcun flag, verranno elencato dopo i filtri in comune il **Aggiungi elemento esistente** la finestra di dialogo e **Apri File** la finestra di dialogo, ma non verrà utilizzato nel **Cerca nei file**  la finestra di dialogo.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|nome|Tipo|Descrizione|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|Rende il filtro di uno dei filtri comuni nel **Cerca nei file** la finestra di dialogo. Nell'elenco di filtri prima dei filtri non è contrassegnata come comuni sono elencati i filtri comuni.|  
|CommonOpenFilesFilter|REG_DWORD|Rende il filtro di uno dei filtri comuni nel **Apri** la finestra di dialogo. Nell'elenco di filtri prima dei filtri non è contrassegnata come comuni sono elencati i filtri comuni.|  
|FindInFilesFilter|REG_DWORD|Elenca il filtro dopo i filtri in comune il **Cerca nei file** la finestra di dialogo.|  
|NotOpenFileFilter|REG_DWORD|Indica che il filtro non viene utilizzato nel **Apri** la finestra di dialogo.|  
|NotAddExistingItemFilter|REG_DWORD|Indica che il filtro non viene utilizzato nel **Aggiungi elemento esistente** la finestra di dialogo.|  
|SortPriority|REG_DWORD|Impostare SortPriority per regolare l'ordine in cui vengono visualizzati i filtri. I valori maggiori di SortPriority vengono visualizzati in precedenza nell'elenco di filtri.|  
  
## <a name="directory-structure"></a>Struttura di directory  
 VSPackage possono inserire le cartelle e file di modello in qualsiasi punto in un disco locale o remoto, fino a quando il percorso è stato registrato tramite l'ambiente di sviluppo integrato (IDE). Tuttavia, per facilitare l'organizzazione, si consiglia la seguente struttura di directory nel percorso di installazione del prodotto.  
  
 \Templates  
  
 \Projects (contiene i modelli di progetto)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (contiene gli elementi del progetto)  
  
 \CLASSE  
  
 \Form  
  
 \Web pagina  
  
 \HelperFiles (contiene i file utilizzati negli elementi di progetto a più file)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [Applicazioni localizzate](../../ide/localizing-applications.md)   
 [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)