---
title: Modelli di elemento di progetto e progetto SharePoint | Documenti Microsoft
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3890d7678fdc50a867e254edbbb7503acbebcd76
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="sharepoint-project-and-project-item-templates"></a>Modelli di progetto e di elementi di progetto SharePoint
  Le sezioni seguenti vengono descritti il progetto SharePoint disponibili e modelli e le modalità di utilizzo dell'elemento di progetto. 
  
##  <a name="project-and-project-item-templates-overview"></a>Cenni preliminari sui modelli di elemento di progetto e di progetto  
 Quando si crea un nuovo progetto di SharePoint in Visual Studio, un progetto SharePoint viene aggiunto alla soluzione insieme a tutti gli elementi di progetto necessari per il tipo di progetto. Ad esempio, se si crea un progetto di Web Part Silverlight, Visual Studio crea una soluzione che contiene un elemento di progetto di Web Part visiva e un elemento di progetto di applicazione Silverlight insieme a tutti i file necessari per gli elementi di progetto. I modelli di progetto vengono utilizzati per aggiungere elementi di progetto a un progetto di SharePoint esistente, ad esempio l'aggiunta di un ricevitore di eventi, una colonna del sito o elenco.  
  
 Per informazioni sui concetti fondamentali di SharePoint, vedere [blocchi predefiniti di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404). Gli utenti avanzati possono creare progetto personalizzato e i modelli di progetto. Per ulteriori informazioni, vedere [estensione del sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project-templates"></a>Modelli di progetto  
 Ecco un elenco di modelli di progetto SharePoint. Per visualizzare i modelli di progetto SharePoint in Visual Studio, nel **nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo sotto **Visual c#** o  **Visual Basic**, quindi scegliere **2010**.  
  
### <a name="sharepoint-2010-project"></a>Progetto SharePoint 2010  
 Il contenuto di un *progetto SharePoint 2010* sono inclusi in ogni modello di progetto SharePoint. Contiene un progetto SharePoint 2010:  
  
-   Un file di progetto.  
  
-   Una pagina delle proprietà di progetto.  
  
-   Oggetto **riferimenti** cartella Elenca tutti i riferimenti all'assembly nel progetto.  
  
-   Oggetto **funzionalità** cartella che contiene un file di configurazione. feature, utilizzato per distribuire le funzionalità in server SharePoint.  
  
-   Oggetto **pacchetto** cartella che contiene un file package. package, utilizzato per distribuire la soluzione in SharePoint.  
  
-   Un file snk (chiave con nome sicuro) che viene utilizzato per firmare l'assembly con un nome sicuro, per la sicurezza avanzata.  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>Web part Silverlight di SharePoint 2010  
 *Web Part Silverlight di SharePoint 2010* progetti consentono di creare web part per SharePoint che consentono di visualizzare le applicazioni Silverlight. Quando si crea il progetto, è possibile specificare se aggiungere una nuova applicazione Silverlight o fare riferimento a uno esistente. Per ulteriori informazioni, vedere [creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e [procedura dettagliata: creazione di una Web Part Silverlight OData che consente di visualizzare per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="sharepoint-2010-visual-web-part"></a>Web part visiva di SharePoint 2010  
 Oggetto *Web Part visiva di SharePoint 2010* progetto include un file di definizione Elements, una **Web Part** elemento e un **controllo utente** elemento. È possibile progettare l'aspetto della web part visiva trascinando o copiando i controlli dalla casella degli strumenti di Visual Studio all'area del controllo utente. Per ulteriori informazioni, vedere [procedura: creare una Web Part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) e [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="import-sharepoint-2010-solution-package"></a>Importa pacchetto di soluzione SharePoint 2010  
 *Importa pacchetto di soluzione SharePoint 2010* progetti consentono di importare tutto o parte di un sito di SharePoint 2010 esistente, esportato in un file di soluzione (con estensione wsp) di SharePoint, in Visual Studio. Una volta importato in Visual Studio, è possibile personalizzare gli elementi e ridistribuirli. Per ulteriori informazioni, vedere [l'importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>Importa flusso di lavoro riutilizzabile di SharePoint 2010  
 *Importare riutilizzabili flusso di lavoro di SharePoint 2010* progetti consentono di importare un flusso di lavoro riutilizzabile e dichiarativo creato in SharePoint Designer 2010 in Visual Studio. Il flusso di lavoro viene esportata dal sito di SharePoint come un file con estensione wsp. Una volta importato in Visual Studio, personalizzarlo, aggiungere il codice e quindi distribuirla in un sito di SharePoint. Per ulteriori informazioni, vedere [procedura dettagliata: importare un flusso di lavoro di SharePoint Designer riutilizzabile in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project-item-templates"></a>I modelli di progetto  
 Ecco un elenco di modelli di elemento di progetto SharePoint. I modelli di progetto aggiungono file alla soluzione di SharePoint per supportare la funzionalità di SharePoint, ad esempio le colonne del sito, elenchi e tipi di contenuto. Ad esempio, l'aggiunta di una colonna del sito per la soluzione aggiunge un progetto di colonna del sito che contiene un file di definizione Elements. Aggiunta di una web part visiva, un progetto di visual web part viene aggiunto alla soluzione che contiene un file Elements.xml, un elemento controllo utente e un elemento web part visiva.  
  
 Per visualizzare i modelli di elemento di progetto SharePoint, in **Esplora**, aprire il menu di scelta rapida per un progetto SharePoint e quindi scegliere **Aggiungi**, **nuovo elemento**. Espandere il **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere **2010**.  
  
### <a name="application-page-farm-solution-only"></a>Pagina dell'applicazione (solo soluzione Farm)  
 Un **pagina dell'applicazione (solo soluzione Farm)** elemento consente di progettare un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagina web per un sito di SharePoint. Pagine di applicazioni è utilizzabile solo nelle soluzioni farm. Solo per soluzioni farm, è possibile aggiungere l'elemento del progetto. Per ulteriori informazioni, vedere [procedura: creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md) e [applicazione layouts tipo pagina](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>Modello di integrazione applicativa dei dati di business (solo soluzione Farm)  
 Oggetto **(solo soluzione Farm) modello di integrazione applicativa dei dati Business** elemento consente di integrare dati di business in SharePoint. Dati di business possono provenire da applicazioni server back-end, ad esempio [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel e Service Advertising Protocol (SAP). Modelli di connettività dei dati aziendali è utilizzabile solo nelle soluzioni farm. Solo per soluzioni farm, è possibile aggiungere l'elemento del progetto. Per ulteriori informazioni, vedere [procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md), [come: utilizzare un File di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), e [novità: applicativa Servizi](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### <a name="content-type"></a>Tipo di contenuto  
 *Tipo di contenuto* elementi consentono di creare tipi di contenuto personalizzati basati su un tipo di contenuto esistente (base), ad esempio un documento, un annuncio o un'attività. Un tipo di contenuto personalizzato fornisce gli stessi attributi e i campi come tipo di contenuto base insieme a tutte le colonne del sito (campi) si definisce. Ad esempio, è possibile creare un tipo di contenuto contatto personalizzato che è in base al tipo di contenuto contatto base fornito in SharePoint. Modificando le colonne del sito esistente o aggiungendo altre colonne del sito a quelli già inclusi nel tipo di contenuto di base, è possibile personalizzare il tipo di contenuto.  
  
> [!NOTE]  
>  A causa di una limitazione di SharePoint, è possibile creare un tipo di contenuto soluzione farm basato sul tipo di contenuto di una soluzione creata mediante sandbox.  
  
 Per ulteriori informazioni, vedere [procedura dettagliata: creazione di una colonna del sito, tipo di contenuto e l'elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [blocco predefinito: tipo di contenuto](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### <a name="empty-element"></a>Elemento vuoto  
 *Gli elementi vuoti* vengono spesso usate per definire gli elementi di progetto SharePoint che non dispongono di un progetto o un modello di elemento di progetto in Visual Studio. Quando si aggiunge un elemento vuoto al progetto, un nodo denominato EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] contiene un singolo file denominato Elements. Utilizzare [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] istruzioni per definire gli elementi desiderati in Elements.  
  
### <a name="event-receiver"></a>Ricevitore di eventi  
 *Ricevitori di eventi* gestire gli eventi per gli elementi nel sito di SharePoint, ad esempio quando un elemento viene aggiunto a un elenco, quando viene eliminato un elemento web o l'avvio di un flusso di lavoro. Il modello di elemento del progetto ricevitore di eventi consente di gestire  
  
-   Elenco eventi  
  
-   Eventi elementi elenco  
  
-   Elenco eventi di posta elettronica  
  
-   eventi Web  
  
-   Elenco eventi di flusso di lavoro  
  
 L'elemento di progetto ricevitore di eventi crea un **ricevitore di eventi** cartella con un singolo file di classe contiene gestori eventi per tutti gli eventi specificato al momento della creazione del progetto nel **personalizzazione di SharePoint Procedura guidata**. La classe del ricevitore di eventi può gestire eventi che si verificano nel sito di SharePoint quando elementi quali file, campi, gli elementi, elenchi, gli allegati, web part e flussi di lavoro vengono aggiunti, aggiornati, eliminati o rimosso. Per ulteriori informazioni, vedere [procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md) e [blocco predefinito: gestione degli eventi](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### <a name="list"></a>List  
 Un elenco è un'istanza di una riutilizzabili base SharePoint definizione di elenco, ad esempio un calendario o un elenco di attività. Dopo aver aggiunto un elenco per la soluzione, la finestra di progettazione di elenco consente di aggiungere all'elenco di colonne del sito e creare le colonne dell'elenco personalizzato. Incluse le colonne del sito da tipi di contenuto. È possibile specificare il *vista* per l'elenco, che determina le colonne che verranno visualizzati nell'elenco. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di una colonna del sito, tipo di contenuto e l'elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) e [blocco predefinito: elenchi e raccolte documenti](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### <a name="module"></a>Modulo  
 *I moduli* (da non confondere con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduli) contiene file che si desidera distribuire nel server SharePoint, ad esempio immagini o note. L'elemento di progetto del modulo contiene un **modulo** nodo. Il nodo del modulo contiene due modelli di elemento di progetto: un file di definizione XML, che funge da un manifesto per il modulo, e un file txt, un file di segnaposto. Per ulteriori informazioni, vedere [utilizzando moduli da includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md) e [moduli](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### <a name="sequential-workflow-farm-solution-only"></a>Flusso di lavoro sequenza (solo soluzione Farm)  
 Oggetto *flusso di lavoro sequenza* è una serie di passaggi di logica di business, eseguite in sequenza, fino a quando non viene completata l'ultimo passaggio. Flussi di lavoro sequenziali vengono utilizzati per gestire i processi che implicano elementi, ad esempio elenchi e documenti di SharePoint. È possibile creare flussi di lavoro a livello di sito (globale) o flussi di lavoro a livello di elenco (locale) e se un flusso di lavoro viene avviata automaticamente o manualmente, è possibile selezionare. Questo elemento di progetto è utilizzabile solo nelle soluzioni farm. Solo per soluzioni farm, è possibile aggiungere l'elemento del progetto. Per ulteriori informazioni, vedere [la creazione di soluzioni flusso di lavoro di SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [flussi di lavoro in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), e [novità: miglioramenti del flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="silverlight-web-part"></a>Web Part Silverlight  
 *Web part Silverlight* elementi di progetto consentono di creare web part per SharePoint che consentono di visualizzare le applicazioni Silverlight. Quando si aggiunge l'elemento del progetto alla soluzione, è possibile scegliere se aggiungere una nuova applicazione Silverlight o fare riferimento a uno esistente in un secondo momento. Per ulteriori informazioni, vedere [creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) e [procedura dettagliata: creazione di una Web Part Silverlight OData che consente di visualizzare per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="site-column"></a>Colonna del sito  
 Oggetto *colonna del sito*, nota anche come un *campo*, uno degli elementi di base è possibile aggiungere a un progetto SharePoint. Una colonna del sito rappresenta un tipo di dati, ad esempio un numero di telefono, un commento di testo o il nome della città di un contatto in un elenco di contatti. Per ulteriori informazioni, vedere [la creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) e [colonne](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### <a name="site-definition-farm-solution-only"></a>Definizione di sito (solo soluzione Farm)  
 *Definizione sito* elementi di progetto contengono una cartella di definizione del sito che include i file seguenti:  
  
-   Una pagina aspx di predefinito, utilizzata come pagina web predefinita per il sito.  
  
-   Un file di onet.xml che definisce i componenti del sito.  
  
-   Un file xml webtemp che specifica le configurazioni di definizione del sito che vengono visualizzati nel **selezione modello** sezione la **nuovo sito di SharePoint** pagina.  
  
 Dopo aver aggiunto una definizione di sito, aggiungere codice e file per fornire funzionalità. Questo elemento di progetto è utilizzabile solo nelle soluzioni farm. Solo per soluzioni farm, è possibile aggiungere l'elemento del progetto. Per ulteriori informazioni, vedere [la creazione di definizioni di sito per SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) e [definizioni di sito e configurazioni](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### <a name="state-machine-workflow-farm-solution-only"></a>Flusso di lavoro macchina a stati (solo soluzione Farm)  
 Oggetto *flusso di lavoro macchina* è un set di stati di logica di business e le transizioni e azioni. I passaggi descritti in un flusso di lavoro macchina non vengono eseguiti in sequenza. al contrario, essi vengono attivati da stati e azioni. Ad esempio un flusso di lavoro sequenza, flussi di lavoro stato macchina sono associati a elementi di SharePoint, ad esempio elenchi e documenti. In questo caso, è possibile creare flussi di lavoro (globale) a livello di sito o a livello di elenco (locale). È anche possibile selezionare se un flusso di lavoro viene avviata automaticamente o manualmente. Questo elemento di progetto è utilizzabile solo nelle soluzioni farm. Solo per soluzioni farm, è possibile aggiungere l'elemento del progetto. Per ulteriori informazioni, vedere [la creazione di soluzioni flusso di lavoro di SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [flussi di lavoro in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), e [novità: miglioramenti del flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="user-control-farm-solution-only"></a>Controllo utente (solo soluzione Farm)  
 Oggetto *controllo utente* è un controllo personalizzato e riutilizzabile in cui è possibile aggiungere altri controlli ASP.NET e SharePoint. Il controllo utente può essere aggiunto alle pagine di applicazione e dalle web part eseguite in SharePoint. Questo elemento di progetto è utilizzabile solo nelle soluzioni farm. Solo per soluzioni farm, è possibile aggiungere l'elemento del progetto. Per ulteriori informazioni, vedere [la creazione di controlli riutilizzabili per Web part o pagine applicazione](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### <a name="visual-web-part"></a>Web Part visiva  
 Oggetto *web part visiva* elemento di progetto include un file di definizione Elements, una **Web Part** elemento e un **controllo utente** elemento. È possibile progettare l'aspetto della web part visiva trascinando o copiando i controlli dalla casella degli strumenti di Visual Studio all'area del controllo utente. Per ulteriori informazioni, vedere [procedura: creare una Web Part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) e [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="web-part"></a>Web part  
 Oggetto *web part* è un controllo sul lato server che viene eseguita all'interno di un tipo speciale di pagina denominata una pagina Web Part. Sono i blocchi predefiniti di pagine visualizzate in un sito di SharePoint. L'elemento web part vengono forniti i file che consentono di progettare una web part per un sito di SharePoint. Per ulteriori informazioni, vedere [procedura: creare una Web Part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) e [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Prodotti e tecnologie SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
