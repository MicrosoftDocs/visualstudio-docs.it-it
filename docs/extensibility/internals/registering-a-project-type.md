---
title: Registrazione di un tipo di progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e6c91f2c92dd121cd135aef4291c7f7983206ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="registering-a-project-type"></a>Registrazione di un tipo di progetto
Quando si crea un nuovo tipo di progetto, è necessario creare le voci del Registro di sistema che consentono a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per riconoscere e usare il tipo di progetto. Queste voci del Registro di sistema è in genere creare utilizzando un file di script (con estensione RGS) del Registro di sistema.  
  
 Nell'esempio seguente, i percorsi predefiniti di fornire le istruzioni dal Registro di sistema e dati, ove applicabile, seguito da una tabella che contiene le voci dello script del Registro di sistema per ogni istruzione. Le tabelle forniscono le voci di script e informazioni aggiuntive sulle istruzioni.  
  
> [!NOTE]
>  Le seguenti informazioni del Registro di sistema deve essere un esempio del tipo e a scopo di voci negli script del Registro di sistema che si scriverà per registrare il tipo di progetto. Le voci effettive e il relativo utilizzo potrebbe variare in base ai requisiti specifici del tipo di progetto. Esaminare gli esempi disponibili per cercare uno che è simile al tipo di progetto che si sviluppa e quindi controllare lo script del Registro di sistema per tale esempio.  
  
 Negli esempi seguenti sono da HKEY_CLASSES_ROOT.  
  
## <a name="example"></a>Esempio  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Nome e una descrizione dei file del tipo di progetto contenenti .figp l'estensione.|  
|`Content Type`|REG_SZ|`Text/plain`|Tipo di contenuto per i file di progetto.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Icona predefinita utilizzata per il progetto di questo tipo. Istruzione % MODULE % viene completata nel Registro di sistema nel percorso predefinito del tipo di progetto DLL.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Applicazione predefinita in cui questo tipo di progetto verrà aperto.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Comando predefinito che verrà eseguito quando viene aperto un progetto di questo tipo.|  
  
 Negli esempi seguenti sono da HKEY_LOCAL_MACHINE e si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
## <a name="example"></a>Esempio  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@` (Impostazione predefinita)|REG_SZ|`FigPrj Project VSPackage`|Nome localizzabile di registrato VSPackage (tipo di progetto).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Percorso del tipo di progetto DLL. L'IDE carica la DLL e passa il CLSID VSPackage per `DllGetClassObject` ottenere <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> per costruire il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> oggetto.|  
|`CompanyName`|REG_SZ|`Microsoft`|Nome della società che ha sviluppato il tipo di progetto.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Nome per il tipo di progetto.|  
|`ProductVersion`|REG_SZ|`9.0`|Rilasciare il numero di versione del tipo di progetto.|  
|`MinEdition`|REG_SZ|`professional`|Edizione del pacchetto VSPackage in corso la registrazione.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Il pacchetto di caricare la chiave per il progetto VSPackage. La chiave viene convalidata quando un progetto viene caricato dopo l'avvio dell'ambiente.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nome file della DLL che contiene le risorse localizzate per il tipo di progetto satellite.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Percorso della DLL satellite.|  
|`FigProjectsEvents`|REG_SZ|Vedere l'istruzione per valore.|Determina la stringa di testo restituita per questo evento di automazione.|  
|`FigProjectItemsEvents`|REG_SZ|Vedere l'istruzione per valore.|Determina la stringa di testo restituita per questo evento di automazione.|  
  
 Tutti gli esempi seguenti si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Esempio  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Nome predefinito di progetti di questo tipo.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID di risorsa del nome da recuperare dalla DLL satellite registrato in pacchetti.|  
|`Package`|REG_SZ|`%CLSID_Package%`|ID di classe del pacchetto VSPackage è registrato in pacchetti.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso predefinito dei file di modello di progetto. Questi sono i file visualizzati tramite il nuovo progetto modello.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Percorso predefinito dei file di modello di elemento di progetto. Questi sono i file visualizzati dal modello di Aggiungi nuovo elemento.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Consente l'IDE implementare il **aprire** la finestra di dialogo.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Utilizzato dall'IDE per determinare se il progetto viene aperto è gestito da questo tipo di progetto (factory del progetto). Il formato per più di una voce è un elenco delimitato da virgola. Ad esempio "vdproj; vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Utilizzato dall'IDE come l'estensione di file predefinita per l'operazione Salva con nome.|  
|`Filter Settings`|REG_DWORD|Varie, vedere le istruzioni e commenti nella tabella seguente.|Queste impostazioni vengono utilizzate per impostare i filtri diversi per la visualizzazione dei file nelle finestre di dialogo dell'interfaccia utente.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID di risorsa per i modelli di Aggiungi elemento.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Percorso degli elementi di progetto visualizzati nella finestra di dialogo per la **Aggiungi nuovo elemento** modello.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Nel nodo della struttura dei file visualizzati nell'ordine determina il **Aggiungi nuovo elemento** la finestra di dialogo.|  
  
 Nella tabella seguente vengono illustrate le opzioni di filtri disponibili nel segmento di codice precedente.  
  
|Opzione di filtro|Descrizione|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Indica che il filtro è uno dei filtri in comune il **Cerca nei file** la finestra di dialogo. I filtri comuni sono elencati nell'elenco di filtri prima dei filtri non è contrassegnata come comuni.|  
|`CommonOpenFilesFilter`|Indica che il filtro è uno dei filtri in comune il **Apri** la finestra di dialogo. I filtri comuni sono elencati nell'elenco di filtri prima dei filtri non è contrassegnata come comuni.|  
|`FindInFilesFilter`|Indica che il filtro può essere uno dei filtri nel **Cerca nei file** finestra di dialogo casella e saranno elencati dopo i filtri comuni.|  
|`NotOpenFileFilter`|Indica che il filtro non verrà usato nel **Apri** la finestra di dialogo.|  
|`NotAddExistingItemFilter`|Indica che il filtro non verrà usato in Aggiungi **elemento esistente** la finestra di dialogo.|  
  
 Per impostazione predefinita, se un filtro non dispone di uno o più di questi flag impostati, viene utilizzato il filtro nel **Aggiungi elemento esistente** la finestra di dialogo e **Apri** la finestra di dialogo dopo che sono elencati i filtri comuni. Il filtro non viene utilizzato nel **Cerca nei file** la finestra di dialogo.  
  
 Tutti gli esempi seguenti si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Esempio  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID di risorsa per i modelli di progetto.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso per i progetti di tipo di progetto registrati predefinito.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Set di ordinamento dei progetti visualizzati nella finestra di dialogo Creazione guidata nuovi progetti.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica che i progetti di questo tipo vengono visualizzati solo nella finestra di dialogo Nuovo progetto.|  
  
 Tutti gli esempi seguenti si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Esempio  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Nessuno|Valore che indica che le voci seguenti siano per le voci di progetti di file esterni.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valore di ID di risorsa per i file di modello di aggiungere nuovi elementi.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Il percorso predefinito degli elementi che verranno visualizzati nel **Aggiungi nuovo elemento** la finestra di dialogo.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Stabilisce l'ordine di visualizzazione nel nodo della struttura ad albero di **Aggiungi nuovo elemento** la finestra di dialogo.|  
  
 Nell'esempio seguente si trova nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Esempio  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 La voce di menu punta l'IDE per la risorsa utilizzata per recuperare le informazioni di menu. Quando questi dati sono stati uniti al database di menu, la stessa chiave verrà aggiunto nella sezione MenusMerged del Registro di sistema. Il pacchetto VSPackage non deve modificare qualsiasi elemento nella sezione MenusMerged direttamente. Nel campo dati nella tabella seguente sono presenti tre valori delimitati da virgole--campi delimitati. Il primo campo identifica un percorso completo di un file di risorse di menu:  
  
-   Se il primo campo viene omesso, la risorsa di menu verrà caricata dal identificato dal GUID VSPackage DLL satellite.  
  
 Il secondo campo che identifica un ID di risorsa di menu di tipo CTMENU:  
  
-   Se è specificato l'ID di risorsa e il percorso del file è specificato dal primo parametro, una risorsa di menu viene caricata dal percorso del file completo.  
  
-   Se è specificato l'ID di risorsa, ma non è il percorso del file, la risorsa di menu viene caricata dalla DLL satellite.  
  
-   Se il percorso completo del file viene fornito e l'ID risorsa è omesso, il file da caricare deve essere un file CTO.  
  
 L'ultimo campo identifica il numero di versione per la risorsa CTMENU. È possibile unire nuovamente il menu modificando il numero di versione.  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|% CLSID_Package %|REG_SZ|`,1000,1`|La risorsa per recuperare le informazioni di menu.|  
  
 Tutti gli esempi seguenti si trovano nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valore di ID di risorsa per i modelli di progetto nuovo progetto di cifre.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso predefinito della directory di nuovi progetti. In questa directory verranno visualizzati nel **Creazione guidata nuovo progetto** la finestra di dialogo.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Stabilisce l'ordine in cui verranno visualizzati nel nodo della struttura dei progetti di **nuovo progetto** la finestra di dialogo.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica che i progetti di questo tipo vengono visualizzati solo nel **nuovo progetto** la finestra di dialogo.|  
  
 Nell'esempio seguente si trova nel Registro di sistema nella chiave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|ID di classe del pacchetto VSPackage registrato.|  
|`UseInterface`|REG_DWORD|`1`|1 indica che l'interfaccia utente da utilizzare per interagire con il progetto. 0 non indica che è presente alcuna interfaccia utente.|  
  
 File VSZ sono controllano spesso i nuovi tipi di progetto contengono una voce RELATIVE_PATH. Questo percorso è relativo al percorso specificato nella voce \ProductDir del tipo di progetto nella chiave del programma di installazione seguente:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Ad esempio, i modelli di progetto di Enterprise Framework aggiungono le voci del Registro di sistema seguenti:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Che indica se si include un PROJECT_TYPE = EF voce nel file VSZ trova l'ambiente del vsz file nella directory ProductDir specificata in precedenza.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)