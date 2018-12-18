---
title: Componenti di base del modello di progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2cfb9db9c354eb4c10ece0f5a8259f3d4a104e28
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="project-model-core-components"></a>Componenti di base del modello di progetto
Espandono le tabelle seguenti nel modello di progetto. Le tabelle presentano brevi descrizioni di interfacce e servizi individuati nel modello e le interfacce e i servizi associati a oggetti specifici. Inoltre, le tabelle in dettaglio le altre interfacce facoltative nella creazione del progetto e di manutenzione a seconda dei requisiti del tipo di progetto specifico.  
  
 Per ulteriori informazioni, vedere [strumenti di esplorazione simbolo supporto](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Oggetto di pacchetto  
  
|Interfaccia|Commenti|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inizializza un pacchetto VSPackage nell'IDE e rende disponibili i servizi all'IDE.|  
  
### <a name="project-factory-object"></a>Oggetto Factory del progetto  
  
|Interfaccia|Commenti|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gestisce la creazione di nuovi progetti e aprire progetti esistenti.|  
  
### <a name="project-objects"></a>Oggetti del progetto  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gestisce l'aggiunta e rimozione di elementi del progetto, consente di aprire gli editor e mantiene i mapping tra ogni moniker del documento e `VSITEMID`. Eredita da `IVsProject` e `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gestisce le proprietà di navigazione e la visualizzazione e fornisce gli eventi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Consente di comando di esecuzione simile a quello di `IOleCommandTarget` per i comandi, ad esempio Taglia e ridenominazione che vengono applicati solo quando lo stato attivo in Esplora soluzioni.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Funge da interfaccia destinazione comando primario per una gerarchia del progetto. È l'interfaccia standard per eseguire query sugli oggetti per i comandi dello stato o di stato e di esecuzione del comando. Disponibile quando non si seleziona nella finestra del progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistenza dello stato del progetto. In genere, lo stato del progetto viene archiviato come file di progetto, ma può essere adattato per sistemi di archiviazione che non sono basati su file.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Consente al progetto gestire tutti gli aspetti della persistenza per i relativi elementi di progetto, come file su disco o oggetti in altri sistemi di archiviazione. Il `IVsPeristHierarchyItem2` interfaccia viene utilizzata per gli elementi che non implementano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaccia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina le interazioni con controllo del codice sorgente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Consente di gestire le informazioni di configurazione dei progetti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gestisce gli oggetti di configurazione di progetto, ad esempio le configurazioni di Debug e rilascio. Compilazione, distribuzione e debug operazioni vengano coordinate tramite gli oggetti di configurazione di progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementato dalle gerarchie per controllare l'eliminazione (distruttiva) o rimuovere le opzioni (non distruttiva) per gli elementi della gerarchia. Chiamare l'interfaccia di Query su di `IVsHierarchyDeleteHandler` interfaccia dal `IVsHierarchy` interfaccia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Offre la possibilità di implementazione di modo che l'oggetto che supporta il `IVsCfgProvider2` interfaccia su un'identità COM diversa da quello dell'oggetto di progetto che implementa il `IVsHierarchy` interfaccia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaccia facoltativa implementato per rendere il progetto estendibile da altri sviluppatori. Il `IVsProjectStartupServices` interfaccia consente a un pacchetto VSPackage di terze parti registrare un GUID da mantenere nel file di progetto in modo che ogni volta che viene caricato il progetto, si caricano il GUID del servizio di terze parti del file di progetto e chiamare `QueryService` per tale GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementato dalle gerarchie di origine in un `UIHierarchy` finestra per coordinare le operazioni sugli Appunti, ad esempio Taglia, copia e Incolla. Utilizzare il `AdviseClipboardHelperEvents` interfaccia di registrazione di eventi negli Appunti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fornisce informazioni su un elemento trascinato rispetto alla relativa origine dati durante un'operazione di trascinamento e rilascio in una finestra gerarchia dell'interfaccia utente. Chiamato dal `IVsHierarchy` interfaccia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fornisce informazioni su un elemento trascinato rispetto alla destinazione di rilascio durante un'operazione di trascinamento e rilascio in una finestra gerarchia dell'interfaccia utente. Chiamato dal `IVsHierarchy` interfaccia.|  
  
### <a name="configuration-object"></a>Oggetto di configurazione  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Vengono fornite informazioni sulla configurazione di.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Consente di gestire le informazioni di configurazione dei progetti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Consente a un progetto essere eseguito sotto il controllo del debugger.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementata da progetti di distribuzione che eseguono operazioni di distribuzione per altri progetti.|  
  
### <a name="configuration-builder-object"></a>Oggetto di configurazione Generatore  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gestisce l'operazione di compilazione della configurazione del progetto.|  
  
### <a name="additional-project-objects"></a>Altri oggetti del progetto  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Consente di visualizzare le proprietà degli elementi di **proprietà** finestra.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Consente di visualizzare l'output per la distribuzione.|  
  
 Nella tabella seguente vengono visualizzate brevi descrizioni di servizi identificati nel modello di progetto.  
  
### <a name="services"></a>Servizi  
  
|Service|Commenti|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Utilizzato dal package VS che implementano i tipi di progetto per registrare che le factory del progetto esista con l'IDE. Il pacchetto VSPackage è necessario chiamare `QueryService` per questo servizio e registrare la factory del progetto quando `IVsPackage::SetSite` viene chiamato. Se il `SetSite` non viene chiamato, il progetto non viene creata un'istanza.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce l'accesso a nozione di incorporato, interno dell'IDE di soluzione corrente, ad esempio la possibilità di enumerare i progetti, creare nuovi progetti, tenere conto di modifiche al progetto e così via.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Chiamato da progetti che si desiderano partecipare al controllo del codice sorgente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Gestisce una tabella dei documenti aperti per determinare se uno o più elementi del progetto sono già aperto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene le interfacce e metodi chiamati per effettivamente di aprire un elemento di progetto utilizzando l'editor standard o un editor specifico.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Deve essere chiamato da tutti i progetti quando aggiungere, rimuovere o rinominare i relativi elementi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gestisce le modifiche apportate a un file o directory e notifica ai client, se i file selezionati sono stati modificati sul disco.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Deve essere chiamato da tutti i progetti e gli editor prima di essere dirty elementi o salvarli.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gestisce l'ordine delle operazioni di compilazione e distribuzione per le configurazioni di progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fornisce l'accesso ai servizi di basso livello debugger utilizzato per la maggior parte dei controlli di debug.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Consente l'accesso a informazioni sulla selezione corrente VSPackage e abilita la comunicazione con il **proprietà** finestra.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce funzionalità IDE correlate all'interfaccia utente di base, ad esempio la possibilità di creare ed enumerare finestre degli strumenti o finestre di documento o segnalare un errore all'utente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Fornisce l'accesso alla barra di stato dell'IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Utilizzato per implementare il modello di automazione. In un modello di progetto, restituirà un oggetto di proprietà che consente di crea un'istanza di tale oggetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Utilizzato per implementare eventi negli Appunti per l'oggetto di progetto nella gerarchia. `SVsUIHierWinClipboardHelper` Consente di correttamente handle Taglia, copia e Incolla operazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Non incluso nella Build: utilizzo delle classi di progetto HierUtil7 implementato un tipo di progetto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Supporto di strumenti di esplorazione di simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)