---
title: Sviluppo di soluzioni SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cf4e6f10d76b29c5bf70ce01d99a2103672ae213
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="developing-sharepoint-solutions"></a>Sviluppo di soluzioni SharePoint
  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono disponibili diversi modelli di tipi di progetto SharePoint per la creazione di siti ed elementi dei siti SharePoint. Per un elenco di tipi di progetto disponibili, vedere [progetto SharePoint e i modelli di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md). Di seguito è riportata una descrizione degli elementi e delle proprietà di un progetto SharePoint.  
  
 Per informazioni su SharePoint 2013 e sui componenti aggiuntivi per SharePoint, vedere le pagine relative a [SharePoint 2013](http://msdn.microsoft.com/library/jj162979.aspx) e alla [compilazione di componenti aggiuntivi per SharePoint](http://msdn.microsoft.com/library/office/apps/jj163230%28v=office.15%29.aspx).  
  
## <a name="elements-of-a-sharepoint-project"></a>Elementi di un progetto SharePoint  
 I nodi di un progetto SharePoint sono noti come *elementi di SharePoint*. Gli elementi di SharePoint possono anche contenere uno o più file correlati, detti *i file di elemento di SharePoint*, ad esempio [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] i file di configurazione, i form ASPX e altro ancora.  
  
 Anziché creare progetti tramite modelli di progetto che sono già popolati con i file degli elementi del progetto, è possibile usare il modello **Progetto vuoto** per creare un progetto SharePoint vuoto e successivamente aggiungervi manualmente gli elementi. I progetti SharePoint possono inoltre contenere anche uno o più file di funzionalità (per l'attivazione in SharePoint) e un file di pacchetto in cui distribuire il progetto.  
  
### <a name="special-nodes"></a>Nodi speciali  
 Ogni progetto SharePoint contiene due nodi che non possono essere rinominati, eliminati, tagliati, copiati o trascinati dal progetto. Questi nodi sono:  
  
-   Funzionalità  
  
-   Pacchetto  
  
 Entrambi i nodi vengono sempre visualizzati in tutti i progetti SharePoint anche se non sono stati definiti pacchetti o funzionalità per il progetto.  
  
#### <a name="features-node"></a>Nodo Funzionalità  
 Il nodo **Funzionalità** contiene una o più funzionalità del progetto SharePoint. Una funzionalità è un contenitore di estensioni per SharePoint. Una volta distribuita nel server SharePoint, una funzionalità può essere inclusa nelle definizioni dei siti o attivata individualmente dagli amministratori di SharePoint nei siti SharePoint. Per altre informazioni, vedere la pagina relativa all' [uso delle caratteristiche](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
 Quando un elemento, ad esempio un tipo di contenuto o un'istanza di elenco, viene aggiunto a un progetto SharePoint, viene anche aggiunto a una funzionalità del nodo **Funzionalità** . L'ambito dell'elemento determina se viene aggiunto a una funzionalità nuova o esistente. Se il nuovo elemento ha lo stesso ambito di una funzionalità esistente, viene aggiunto a tale funzionalità. In caso contrario, l'elemento viene aggiunto a una nuova funzionalità.  
  
 Per aggiungere manualmente una funzionalità, eseguire il comando **Aggiungi funzionalità** dal menu di scelta rapida del nodo della funzionalità. Mediante la finestra di progettazione delle funzionalità, è possibile visualizzare o modificare il contenuto di una funzionalità. Per ulteriori informazioni, vedere [procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
 Quando una funzionalità viene aggiunta a un progetto SharePoint, viene visualizzata in **Esplora soluzioni** come nodo con il nome predefinito Feature*x*.feature, dove *x* è un numero univoco. Dopo che una funzionalità viene distribuita nel server SharePoint, un amministratore di SharePoint può attivarla e renderla disponibile agli utenti del sito SharePoint.  
  
#### <a name="package-node"></a>Nodo Pacchetto  
 Il nodo **Pacchetto** contiene un singolo file che serve come meccanismo di distribuzione per il progetto SharePoint. Questo file, noto come un *soluzione * * pacchetto*, è. Basato su CAB con una. Estensione WSP. Un pacchetto della soluzione è un file distribuibile e riutilizzabile che contiene un set di funzionalità, definizioni dei siti e assembly che è possibile applicare ai siti SharePoint, nonché abilitare o disabilitare individualmente. Il **pacchetto** nodo contiene sempre anche un file denominato package. wspdef, un [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file di definizione per il pacchetto. Quando un pacchetto viene distribuito nel server che esegue SharePoint, l'amministratore di SharePoint può installarlo e attivare le relative funzionalità.  
  
 È possibile visualizzare o modificare il contenuto del pacchetto in Progettazione pacchetti facendo doppio clic sul nodo del pacchetto o aprendo il relativo menu di scelta rapida e scegliendo **aprire**. Per ulteriori informazioni, vedere [la creazione di pacchetti della soluzione SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
## <a name="sharepoint-project-and-project-item-properties"></a>Proprietà dei progetti e degli elementi di progetto SharePoint  
 Nei progetti SharePoint, come in qualsiasi altro progetto di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le proprietà sono visualizzate nella finestra Proprietà e nella pagina delle proprietà. Le proprietà visualizzate dipendono dal nodo selezionato.  
  
 Quando un progetto, un elemento di progetto o un nodo del file dell'elemento di progetto SharePoint viene selezionato in **Esplora soluzioni**, nella finestra Proprietà o nella pagina delle proprietà vengono visualizzate le proprietà seguenti:  
  
### <a name="project-properties"></a>Proprietà progetto  
  
|Nome proprietà|Descrizione|  
|-------------------|-----------------|  
|Configurazione distribuzione attiva|Specifica la serie di passaggi eseguiti durante la distribuzione. Per ulteriori informazioni, vedere [procedura: modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|  
|Destinazione distribuzione assembly|Determina dove si trovano gli *assembly di applicazione di SharePoint* . I valori validi per la posizione degli assembly sono *GlobalAssemblyCache* (valore predefinito) o *WebApplication*.<br /><br /> Se la proprietà *Sandboxed Solution* è impostata su **true**, questa proprietà è disabilitata.|  
|Ritrazione automatica dopo il debug|Specifica se la soluzione distribuita viene ritratta automaticamente da SharePoint dopo l'esecuzione dell'applicazione in modalità di debug in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Quando la proprietà è selezionata, la soluzione viene ritratta quando l'IDE ritorna alla visualizzazione Progettazione dopo il debug. Quando non è selezionata, la soluzione non viene ritratta. Per altre informazioni, vedere [Ritrazione di una soluzione](http://go.microsoft.com/fwlink/?LinkId=183819).|  
|Modifica configurazioni|Specifica la configurazione di distribuzione da usare per il progetto. Per ulteriori informazioni, vedere [procedura: modificare una configurazione di distribuzione di SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) e [distribuzione, pubblicazione e l'aggiornamento di pacchetti della soluzione SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|  
|Abilita debug Silverlight (anziché il debug degli script)|Quando la proprietà è selezionata, il debugger di Silverlight si connette al processo di debug. Quando non è selezionata, il debugger di script si connette al processo di debug. Per altre informazioni, vedere [Cenni preliminari sul debug di Silverlight](http://go.microsoft.com/fwlink/?LinkId=179826).|  
|Includi assembly in pacchetto|Specifica se l'assembly del progetto viene incluso o meno in un pacchetto in fase di compilazione.|  
|Riga di comando post-distribuzione|Specifica i comandi da eseguire dopo avere distribuito la soluzione SharePoint. Questa riga supporta qualsiasi comando batch, nonché la risoluzione delle variabili MSBuild. Per ulteriori informazioni, vedere [procedura: impostare i comandi di distribuzione di SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Riga di comando pre-distribuzione|Specifica i comandi da eseguire prima della distribuzione della soluzione SharePoint. Questa riga supporta qualsiasi comando batch, nonché la risoluzione delle variabili MSBuild. Per ulteriori informazioni, vedere [procedura: impostare i comandi di distribuzione di SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|File di progetto|Nome del file contenente le informazioni sul progetto relative alla compilazione, alla configurazione e altro.|  
|Cartella di progetto|Posizione del file di progetto nel sistema (sola lettura).|  
|Sandboxed Solution|Specifica se il progetto deve essere distribuito come *soluzione in modalità sandbox*, nota anche come *soluzione creata dall'utente*. Le soluzioni in modalità sandbox non sono necessariamente attendibili. Un valore **true** indica che il progetto è distribuito come soluzione in modalità sandbox, mentre un valore **false** indica che il progetto è distribuito come soluzione farm. Per ulteriori informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md) e [le differenze tra creata mediante sandbox e soluzioni Farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|  
|URL sito|Specifica l'[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] del sito di destinazione per il progetto.|  
|Elemento di avvio|Specifica il primo elemento del progetto da eseguire.|  
  
 Quando si seleziona un file di elemento di SharePoint (ad esempio un flusso di lavoro o una funzionalità nel nodo Funzionalità), nella finestra Proprietà vengono visualizzate le proprietà seguenti:  
  
### <a name="project-item-properties"></a>Proprietà dell'elemento di progetto  
  
|Nome proprietà|Descrizione|  
|-------------------|-----------------|  
|Risoluzione dei conflitti di distribuzione|Specifica l'azione da eseguire quando si distribuisce un elemento del progetto le cui proprietà sono identiche a quelle di un elemento già presente nel server. Per ulteriori informazioni, vedere [risoluzione dei problemi di SharePoint e distribuzione di pacchetti](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|  
|Proprietà funzionalità|Specifica un set di valori (archiviati come coppie chiave/valore) incluso in una funzionalità al momento della distribuzione in SharePoint. Dopo la distribuzione della funzionalità, è possibile accedere ai valori della proprietà nel codice. Per ulteriori informazioni, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Ricevitore di funzionalità|Fornisce il codice eseguito quando si verificano determinati eventi nella funzionalità che contiene un elemento di progetto. Per ulteriori informazioni, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Nome cartella|Nome della cartella dell'elemento di progetto SharePoint.|  
|Riferimenti all'output del progetto|Specifica una dipendenza, ad esempio un assembly, che l'elemento di progetto deve eseguire. Per ulteriori informazioni, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Voci di controllo sicure|Specifica i controlli che gli utenti non attendibili possono modificare senza problemi per la sicurezza. Per ulteriori informazioni, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
  
### <a name="project-item-file-properties"></a>Proprietà del file dell'elemento di progetto  
  
|Nome proprietà|Descrizione|  
|-------------------|-----------------|  
|Azione di compilazione|Specifica la relazione tra il file e i processi di compilazione e distribuzione. Per altre informazioni, vedere [Proprietà file](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Copia nella directory di output|Specifica se i file di origine verranno copiati nella directory di output. Il valore può essere uno dei seguenti:<br /><br /> -   *Non copiare*<br />-   *Copia sempre*<br />-   *Copia se più recente*<br /><br /> Per altre informazioni, vedere [Proprietà file](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Strumento personalizzato|Specifica il nome di uno strumento, se presente, che trasforma il file in fase di progettazione e inserisce l'output della trasformazione in un altro file. Ad esempio, un file di set di dati (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) ha uno strumento personalizzato predefinito. Per altre informazioni, vedere [Proprietà file](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Spazio dei nomi dello strumento personalizzato|Spazio dei nomi in cui viene copiato l'output dello strumento personalizzato. Per altre informazioni, vedere [Proprietà file](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Percorso di distribuzione|Percorso completo del file nel server SharePoint. Questo percorso è composto dalle sottoproprietà Radice distribuzione e Percorso distribuzione|  
|Percorso distribuzione|Il percorso relativo del file nel file del SharePoint Server, ad esempio Workflow1\\. Il percorso completo per il file viene creato concatenando il valore *Deployment Path* alla fine del valore *Deployment Root* .<br /><br /> Selezionare un valore di *RootFile* per il *tipo di distribuzione* le modifiche alle proprietà di *radice distribuzione* in {SharePointRoot}\\, risultante in un percorso completo {SharePointRoot} \Workflow1\\. Per ulteriori informazioni, vedere [sui pacchetti e distribuzione di soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|  
|Deployment Root|Stringa. Cartella radice in cui viene distribuito il file nel server SharePoint. Ad esempio, {SharePointRoot} \Template\Features\\{FeatureName}\\.<br /><br /> Il valore della proprietà *Deployment Root* è determinato dall'impostazione di *Deployment Type* .|  
|Deployment Type|Tipo di distribuzione del file, che determina il valore di *Deployment Root* . Il valore può essere uno dei seguenti:<br /><br /> NoDeployment: \<nessun valore ><br /><br /> Elemento ElementManifest: {SharePointRoot} \Template\Features\\{FeatureName}\\<br /><br /> ElementFile: {SharePointRoot} \Template\Features\\{FeatureName}\\<br /><br /> TemplateFile: {SharePointRoot} \Template\\<br /><br /> RootFile: {SharePointRoot}\\<br /><br /> GlobalResource: \Resources {SharePointRoot}\\<br /><br /> ClassResource: {ClassResourcePath}\\<br /><br /> Per altre informazioni, vedere <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|  
|Nome file|Nome del file o della cartella per il file dell'elemento.|  
|Percorso completo|Percorso del file per l'elemento (sola lettura).|  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)|Descrive i modelli di progetto e di elementi di progetto SharePoint disponibili in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Procedura: Aggiungere elementi a un progetto SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Descrive come aggiungere elementi nuovi o esistenti a un progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Illustra la procedura dettagliata per creare un campo personalizzato, un tipo di contenuto, una definizione di elenco e un'istanza di elenco.|  
|[Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)|Viene descritto come aggiungere un ricevitore di eventi per il progetto creato [procedura dettagliata: creazione di una colonna del sito, tipo di contenuto e l'elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|  
|[Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|Descrive come creare progetti flusso di lavoro che includono form di associazione del flusso di lavoro e form di avvio del flusso di lavoro.|  
|[Creazione di pagine per SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Descrive come creare pagine come pagine dell'applicazione, pagine del sito, pagine master e layout di pagina per SharePoint.|  
|[Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Descrive come aggiungere controlli che consentono agli utenti di modificare direttamente il contenuto, l'aspetto e il comportamento delle pagine del sito SharePoint tramite un browser.|  
|[Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Descrive come creare controlli utente che possono essere utilizzati dalle pagine applicazione e dalle web part eseguite in SharePoint.|  
|[Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Descrive come integrare dati dei servizi Web e delle applicazioni server di back-end in un'applicazione di SharePoint.|  
|[Creazione di definizioni di sito per SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Descrive come creare definizioni di sito, ovvero modelli usati per creare i siti SharePoint.|  
|[Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Descrive come importare elementi, come moduli e tipi di contenuto, da un sito SharePoint esistente in un progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Uso di moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Descrive come usare i moduli per la distribuzione di file dal progetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] al sito SharePoint.|  
|[Esplorazione di connessioni di SharePoint tramite Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Descrive come trovare siti SharePoint locali tramite Esplora Server.|  
|[Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Descrive come usare le proprietà dell'elemento di progetto per fornire informazioni sulla creazione di pacchetti e sulla distribuzione per i progetti, ad esempio voci di controllo sicure, riferimenti all'output del progetto e proprietà delle funzionalità.|  
|[Procedura: Aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Descrive in che modo le cartelle mappate possono essere aggiunte al progetto per semplificare l'accesso alle risorse di SharePoint.|  
|[Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md)|Descrive i problemi associati alle soluzioni in modalità sandbox.|  
|[Sicurezza per le soluzioni SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|Descrive le considerazioni sulla sicurezza relative allo sviluppo di soluzioni SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Finestra di dialogo di selezione URL &#40;sviluppo per SharePoint in Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Descrive una finestra di dialogo che è possibile usare per aggiungere riferimenti di percorso alle risorse nel progetto o nel server SharePoint locale.|  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione al &#40;sviluppo per SharePoint in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)   
 [Esplorazione di connessioni di SharePoint tramite Esplora Server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  