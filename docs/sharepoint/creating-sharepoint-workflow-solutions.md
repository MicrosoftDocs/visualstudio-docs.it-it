---
title: Creazione di soluzioni flusso di lavoro SharePoint | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: bb0dce0aa162260ca784593ec34ee5c39acd1f31
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="creating-sharepoint-workflow-solutions"></a>Creazione di soluzioni flusso di lavoro SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]fornisce strumenti che consentono di creare flussi di lavoro personalizzati che gestiscono il ciclo di vita dei documenti e voci di elenco in un sito Web di SharePoint. Gli elementi forniti prevedono una finestra di progettazione, un set di controlli dell'attività e i riferimenti all'assembly necessari. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]include anche il **Personalizzazione guidata SharePoint**, per creare e configurare i flussi di lavoro.  
  
 Per un elenco di prerequisiti per la creazione di progetti SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md). Per ulteriori informazioni su SharePoint, vedere [Microsoft SharePoint Products and Technologies](http://go.microsoft.com/fwlink/?LinkId=178470).  
  
## <a name="workflows-in-sharepoint"></a>Flussi di lavoro in SharePoint  
 Quando si aggiunge un flusso di lavoro a una raccolta di SharePoint o un elenco, si applica un processo di business in tutti gli elementi nell'elenco o raccolta. Un flusso di lavoro vengono descritte le azioni che il sistema o gli utenti devono eseguire su ogni elemento, ad esempio l'invio dell'elemento da modificare e quindi esaminato. Queste azioni, note come *attività*, sono i blocchi predefiniti del flusso di lavoro.  
  
 È possibile creare flussi di lavoro di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e distribuirli a un sito Web di SharePoint. Dopo aver distribuito un flusso di lavoro in SharePoint, è associarlo a una libreria o elenco. Può quindi essere avviato automaticamente, da un processo o manualmente dall'utente. Per ulteriori informazioni sull'operazione di flusso di lavoro, vedere [utilizzando i flussi di lavoro per gestire i processi](http://go.microsoft.com/fwlink/?LinkId=79757).  
  
## <a name="creating-custom-sharepoint-workflows"></a>Creazione di flussi di lavoro SharePoint personalizzato  
 Due progetti di flusso di lavoro di SharePoint sono disponibili in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **flusso di lavoro sequenziale** e **flusso di lavoro macchina**.  
  
 Oggetto *flusso di lavoro sequenza* rappresenta una serie di passaggi. Le operazioni vengono eseguite una dopo l'altra fino a quando non viene completata l'ultima attività. Flussi di lavoro sequenziali sono sempre strettamente sequenziale la loro esecuzione. Poiché possono ricevere eventi esterni e includere flussi logici paralleli, l'ordine di esecuzione esatto può variare. Nella figura seguente viene illustrato un esempio di flusso di lavoro sequenza.  
  
 ![Flusso di lavoro sequenza](../sharepoint/media/sp-sequential.png "flusso di lavoro sequenza")  
  
 Oggetto *flusso di lavoro macchina* rappresenta un set di stati e transizioni e azioni. I passaggi descritti in un flusso di lavoro macchina eseguono in modo asincrono. Ciò significa che non vengono necessariamente eseguite una dopo l'altra, ma che invece vengono attivate da stati e azioni. Viene assegnato uno stato iniziale e quindi, in base a un evento, si verifica una transizione a un altro stato. La macchina a stati può avere uno stato finale che determina la fine del flusso di lavoro. Il diagramma seguente mostra un esempio di un flusso di lavoro macchina.  
  
 ![Stato del flusso di lavoro macchina](../sharepoint/media/sp-state.png "stato flusso di lavoro macchina")  
  
 Per ulteriori informazioni sui tipi di flusso di lavoro, vedere [tipi di flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=178995).  
  
### <a name="using-the-wizard"></a>Utilizzo della procedura guidata  
 Quando si crea un progetto flusso di lavoro di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], è innanzitutto specificare le impostazioni di **Personalizzazione guidata SharePoint**. La procedura guidata utilizza queste impostazioni per creare un progetto in **Esplora**. Questo progetto contiene un file di codice, diversi file che vengono usate per distribuire il flusso di lavoro e riferimenti agli assembly necessari per creare un flusso di lavoro di SharePoint personalizzata.  
  
 Dopo aver creato il flusso di lavoro, è possibile modificarne le proprietà nella finestra Proprietà. Sebbene la maggior parte delle proprietà del flusso di lavoro possono essere modificate direttamente nella finestra Proprietà, alcune richiedono è possibile fare clic sul pulsante con i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) per modificare i relativi valori. Questo pulsante consente di riavviare il **Personalizzazione guidata SharePoint**. Dopo aver apportato la proprietà valore modifiche, scegliere il **fine** pulsante per renderle effettive.  
  
> [!NOTE]  
>  Il **tipo flusso di lavoro** proprietà è di sola lettura e non può essere modificata. Se si desidera modificare il tipo di flusso di lavoro, è necessario creare un altro flusso di lavoro.  
  
## <a name="designing-a-sharepoint-workflow"></a>Progettazione di un flusso di lavoro di SharePoint  
 Dopo aver definito tutti i passaggi nel processo di business, utilizzare il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Progettazione flussi di lavoro per la progettazione del flusso di lavoro di SharePoint. Per aprire la finestra di progettazione, fare doppio clic su Workflow1.cs o Workflow1. vb in **Esplora**, o aprire il menu di scelta rapida per uno di questi file e quindi scegliere **aprire**.  
  
### <a name="activities"></a>Attività  
 Per progettare un flusso di lavoro, aggiungere le attività dal **della casella degli strumenti** per un *pianificazione del flusso di lavoro* nella finestra di progettazione. Una pianificazione del flusso di lavoro contiene la sequenza di attività nell'ordine che deve essere eseguite.  
  
 Esistono due tipi di attività:  
  
-   *Le attività semplici* eseguire una singola unità di lavoro, ad esempio "ritarda per un giorno" o "Avvia il servizio Web".  
  
-   *Le attività composte* contenere altre attività, ad esempio, un'attività condizionale potrebbe contenere due rami.  
  
 Sono disponibili in entrambi i tipi di attività di **della casella degli strumenti**.  
  
 Attività possono avere una proprietà, metodi ed eventi. Utilizzare il **proprietà** finestra per impostare le proprietà di un'attività.  
  
 È anche possibile creare un'attività personalizzata. Per ulteriori informazioni, vedere [procedura dettagliata: creare un'attività di flusso di lavoro del sito personalizzato](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).  
  
 Le attività sono organizzate nelle seguenti schede di **della casella degli strumenti**:  
  
-   **Flusso di lavoro SharePoint**  
  
-   **Windows Workflow v 3.0**  
  
-   **Windows Workflow v 3.5**  
  
 Non tutte le attività del flusso di lavoro di base sono supportate da SharePoint. Per ulteriori informazioni, vedere [Cenni preliminari sulle attività del flusso di lavoro per Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### <a name="sharepoint-workflow-activities"></a>Attività del flusso di lavoro di SharePoint  
 Il **flusso di lavoro SharePoint** schede contengono le attività specializzate per l'utilizzo in [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Queste attività semplificano lo sviluppo di flussi di lavoro ciclo di vita dei documenti. Per ulteriori informazioni sulle attività elencate nel **flusso di lavoro SharePoint** scheda, vedere [Cenni preliminari sulle attività del flusso di lavoro per Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### <a name="windows-workflow-activities"></a>Attività del flusso di lavoro di Windows  
 Il **Windows Workflow** schede contengono le attività fornite dal [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. È possibile utilizzare queste attività per creare pianificazioni di flusso di lavoro per qualsiasi tipo di applicazione del flusso di lavoro di Windows.  
  
 Per ulteriori informazioni sulle attività elencate nel **flussi di lavoro di Windows** scheda, vedere [attività Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=156096). Per ulteriori informazioni su Windows Workflow Foundation, vedere [Windows Workflow Foundation Overview](http://go.microsoft.com/fwlink/?LinkID=128632).  
  
### <a name="working-with-activities-in-the-designer"></a>Utilizzo delle attività nella finestra di progettazione  
 La pianificazione del flusso di lavoro può contenere una combinazione di attività del flusso di lavoro di Windows e le attività del flusso di lavoro di SharePoint.  
  
 La finestra di progettazione vengono visualizzati indicatori visivi che consentono di posizionare e configurare correttamente le attività. Quando si trascina o si copia un'attività nella pianificazione del flusso di lavoro, nella finestra di progettazione vengono visualizzate delle icone con il segno di addizione (+) in verde che indicano le posizioni valide per quell'attività nel flusso di lavoro. È possibile posizionare un'attività in una posizione in cui non sarebbe valido. Ad esempio, è possibile posizionare un'attività Send come prima attività in un ramo di attività di ascolto. Per ulteriori informazioni, vedere [Centro per sviluppatori di SharePoint Designer](http://go.microsoft.com/fwlink/?LinkId=178476).  
  
## <a name="collecting-information-during-the-workflow"></a>Raccolta delle informazioni durante il flusso di lavoro  
 È possibile raccogliere informazioni dagli utenti in determinati momenti nel flusso di lavoro. È possibile raccogliere informazioni tramite moduli o le proprietà dell'elemento.  
  
### <a name="forms"></a>Moduli  
 I moduli sono come le finestre di dialogo contenenti domande che consentono agli utenti di fornire risposte.  
  
 Esistono quattro tipi di form che può essere usato in un flusso di lavoro:  
  
-   Associazione  
  
-   Avvio  
  
-   Modifica  
  
-   Attività  
  
 Le opzioni [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include modelli di elemento per il form di associazione e di avvio. Un esempio di un *form di associazione* è uno che consente all'amministratore di installare il flusso di lavoro immettere i parametri relativi al flusso di lavoro, ad esempio un limite di spesa per un flusso di lavoro. Un esempio di un *form di avvio* è una classe che consente all'utente di un flusso di lavoro di spesa di immettere l'importo speso nel flusso di lavoro. Per ulteriori informazioni su questi tipi di moduli, vedere [progetto SharePoint e i modelli di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
### <a name="item-properties"></a>Proprietà dell'elemento  
 È anche possibile raccogliere informazioni da utenti con le proprietà di un elemento nell'elenco o raccolta di SharePoint. File di codice principale (Workflow1.cs o Workflow1. vb) dichiara un'istanza della classe Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties denominata `workflowProperties`. Utilizzare il `workflowProperties` oggetto per accedere alle proprietà della libreria o dell'elenco nel codice. Per un esempio, vedere [procedura dettagliata: creazione e debug di una soluzione del flusso di lavoro di SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).  
  
## <a name="debugging-a-sharepoint-workflow-template"></a>Debug di un modello di flusso di lavoro SharePoint  
 È possibile eseguire il debug un progetto flusso di lavoro di SharePoint uguale a quello di altri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetti Web. Quando si avvia il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizza le impostazioni specificate nella **Personalizzazione guidata SharePoint** per aprire il sito Web di SharePoint appropriato e associare automaticamente il modello di flusso di lavoro con la libreria appropriata o elenco. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Collega anche il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger il [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] processo denominato w3wp.exe.  
  
 Per testare il flusso di lavoro, è necessario avviarlo manualmente. Per ulteriori informazioni, vedere la sezione "Debug dei flussi di lavoro" in [debug delle soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Per ulteriori informazioni su [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debug delle applicazioni Web, vedere [Script e il debug di applicazioni Web](/visualstudio/debugger/debugging-web-applications-and-script).  
  
## <a name="deploying-a-sharepoint-workflow-template"></a>Distribuzione di un modello di flusso di lavoro SharePoint  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Distribuire progetti di flusso di lavoro di SharePoint come qualsiasi altro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetti SharePoint. Per ulteriori informazioni, vedere [sui pacchetti e distribuzione di soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).  
  
## <a name="importing-globally-reusable-workflows"></a>L'importazione di flussi di lavoro riutilizzabile globalmente  
 Oltre a creare flussi di lavoro riutilizzabili specifiche del sito, SharePoint Designer consente di creare *flussi di lavoro riutilizzabile globalmente*, che sono flussi di lavoro che può essere utilizzati da qualsiasi sito di SharePoint. Il progetto Importa flusso di lavoro riutilizzabile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attualmente non è possibile importare flussi di lavoro riutilizzabile globalmente. Tuttavia, è possibile utilizzare SharePoint Designer per convertire un flusso di lavoro riutilizzabile globalmente in un flusso di lavoro riutilizzabile, o importare il flusso di lavoro come un flusso di lavoro dichiarativo non convertito. Per ulteriori informazioni, vedere [l'importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura dettagliata: creazione e debug di una soluzione flusso di lavoro SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Illustra la procedura dettagliata Creazione e il debug di un semplice [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] flusso di lavoro.|  
|[Procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Illustra la procedura dettagliata per la creazione di una più completa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] flusso di lavoro completato con form di associazione e di avvio.|  
|[Procedura dettagliata: aggiungere una pagina dell'applicazione a un flusso di lavoro](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Si basa sull'argomento [procedura dettagliata: creazione di un flusso di lavoro con form di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) mediante l'aggiunta di una pagina di applicazione aspx aggiuntivo che fornisce un report sui dati immessi nel flusso di lavoro.|  
|[Procedura dettagliata: creare un'attività personalizzata per un flusso di lavoro del sito](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Viene illustrato come eseguire due attività principali: creare un flusso di lavoro a livello di sito e creare un'attività flusso di lavoro personalizzato.|  
|[Procedura dettagliata: importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Viene illustrato come importare flussi di lavoro dichiarativi riutilizzabili creati in SharePoint Designer 2010 in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)  
  
  