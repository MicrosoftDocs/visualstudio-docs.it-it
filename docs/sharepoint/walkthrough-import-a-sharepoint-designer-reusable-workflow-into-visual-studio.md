---
title: 'Procedura dettagliata: Importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 443502fdb6b018772e4dde833c5d53d27a68dbe8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Procedura dettagliata: Importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio
  Questa procedura dettagliata viene illustrato come importare un flusso di lavoro riutilizzabile creati in SharePoint Designer 2010 in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto flusso di lavoro di SharePoint.  
  
 Flussi di lavoro creati in SharePoint Designer, o *flussi di lavoro dichiarativi*, costituiti da [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] istruzioni anziché codice. SharePoint Designer 2010 introduce *flussi di lavoro riutilizzabili*, che sono portabili e dichiarativi flussi di lavoro può essere utilizzati da diversi elenchi nei siti di SharePoint.  
  
 Flussi di lavoro creati [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], ad esempio i flussi di lavoro macchina a stati e sequenziali, vengono chiamati *flussi di lavoro di codice*. I flussi di lavoro di codice sono costituiti da file XML e i moduli di codice in cui gli utenti possono personalizzare il comportamento del flusso di lavoro.  
  
 Tramite Visual Studio è possibile importare flussi di lavoro riutilizzabili creati in SharePoint Designer 2010 e convertirli in flussi di lavoro di codice per utilizzarli nei siti di SharePoint.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di un flusso di lavoro semplice, riutilizzabile in SharePoint Designer.  
  
-   Esportare il flusso di lavoro riutilizzabile di SharePoint Designer in un file con estensione wsp e in SharePoint.  
  
-   L'importazione del file con estensione wsp in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tramite il progetto Importa flusso di lavoro riutilizzabile.  
  
-   Modifica il flusso di lavoro tramite l'aggiunta di codice.  
  
-   Tramite il flusso di lavoro importato in un sito di SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Le edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## <a name="create-target-sharepoint-subsites"></a>Creare siti secondari di SharePoint di destinazione  
 È innanzitutto necessario creare due nuovi siti secondari di SharePoint: uno per ospitare i flussi di lavoro riutilizzabile di SharePoint Designer, un'altra per ospitare i flussi di lavoro convertiti.  
  
#### <a name="to-create-sharepoint-subsites"></a>Per creare siti secondari di SharePoint  
  
1.  In SharePoint Designer 2010, nella barra dei menu, scegliere **File**, **nuovo sito Web vuoto**.  
  
2.  Nel **nuovo sito Web vuoto** nella finestra di dialogo Sfoglia in un sito di SharePoint in cui si desidera creare il flusso di lavoro oppure utilizzare il valore di http://*NomeSistema*/ e quindi scegliere il **OK** pulsante.  
  
     Verrà visualizzata la Home page.  
  
3.  Nel **siti secondari** , scegliere il **New** pulsante.  
  
4.  Nel **nuovo** finestra di dialogo scegliere **modelli SharePoint** dall'elenco nel riquadro a sinistra, scegliere **sito del Team** dall'elenco nel riquadro di destra.  
  
5.  Nel **specificare il percorso del sito Web** , sostituire la parola **secondario** nell'URL con **SPD1**, quindi scegliere il **OK** pulsante.  
  
     Verrà aperto il nuovo sito secondario in SharePoint Designer. Chiudere l'istanza di SharePoint Designer e tornare alla prima istanza (sito di livello superiore).  
  
6.  Ripetere i passaggi da 3 a 5 per creare il secondo sito secondario, questa volta sostituendo la parola **secondario** nel [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] con **SPD2**.  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Creare un flusso di lavoro riutilizzabile di SharePoint Designer  
 Poiché SharePoint non include tutti i flussi di lavoro riutilizzabile che è possibile utilizzare per questo esempio, si creerà uno. In questo flusso di lavoro semplice, quando un utente immette una nuova attività nell'elenco attività con un titolo specifico, l'attività viene assegnato a tale utente.  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Per creare un flusso di lavoro riutilizzabile di SharePoint Designer  
  
1.  Nel **siti secondari** , scegliere il **SPD1** sito per modificarlo.  
  
2.  Sulla barra multifunzione, scegliere il **flusso di lavoro riutilizzabile** pulsante.  
  
     Verrà visualizzata la procedura guidata Crea flusso di lavoro riutilizzabile.  
  
3.  Nel **nome** immettere **SPD Task Workflow**.  
  
4.  Nel **tipo di contenuto** scegliere **attività**, quindi scegliere il **OK** pulsante.  
  
     Il flusso di lavoro viene aperto nella finestra di progettazione del flusso di lavoro SharePoint Designer.  
  
5.  Nella finestra di progettazione del flusso di lavoro, scegliere il passaggio 1, quindi, sulla barra multifunzione, il **condizione** pulsante.  
  
6.  Nell'elenco delle condizioni, scegliere **se campo della voce corrente è uguale al valore**.  
  
     Questo passaggio viene aggiunta una condizione denominata **se campo è uguale al valore**.  
  
7.  Nel **se campo è uguale al valore** condizione, scegliere il **campo** collegamento.  
  
8.  Nell'elenco di valori, scegliere **titolo**.  
  
9. Nel **se campo è uguale al valore** condizione, scegliere il **valore** collegamento.  
  
10. Nella casella immettere **nuova attività**.  
  
     Legge l'istruzione condizionale ora **se corrente: titolo dell'elemento uguale a nuova attività**.  
  
11. Scegliere la riga sotto l'istruzione condizionale, quindi, sulla barra multifunzione, il **azione** pulsante.  
  
12. Nell'elenco di azioni, scegliere **campo del Set nell'elemento corrente**.  
  
13. Nel **Set campo valore** azione, scegliere il **campo** collegamento e quindi nell'elenco, scegliere **assegnato a**.  
  
14. Nel **Set campo valore** azione, scegliere il **valore** collegamento e quindi nell'elenco di utenti e gruppi esistenti, scegliere **utente che ha creato l'elemento**.  
  
15. Scegliere il **Aggiungi** e quindi scegliere il **OK** pulsante.  
  
     Istruzione dell'azione è ora **imposta assegnato a per elemento corrente: CreatedBy**.  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>Salvare e distribuire il flusso di lavoro riutilizzabile  
 Poiché [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] possibile importare solo i file con estensione wsp, è necessario salvare il flusso di lavoro riutilizzabile come file con estensione wsp e distribuirlo a SharePoint prima di importarli in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Se si riceve un errore di runtime di eseguire la procedura seguente, è necessario eseguire la procedura in un sistema che ha accesso al sito di SharePoint.  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Per salvare e distribuire il flusso di lavoro riutilizzabile  
  
1.  Nella parte superiore della finestra di progettazione di SharePoint, scegliere il **salvare** pulsante per salvare lo stato di avanzamento e quindi scegliere il **pubblica** per distribuire il flusso di lavoro di **SPD1** sito di SharePoint .  
  
2.  Nel riquadro di spostamento, scegliere il **flussi di lavoro** oggetto.  
  
3.  In **flusso di lavoro riutilizzabile**, scegliere **SPD Task Workflow**.  
  
4.  Sulla barra multifunzione, scegliere il **Salva come modello** pulsante per salvare il flusso di lavoro come file con estensione wsp.  
  
5.  Aprire il **SPD1** sito di SharePoint in un browser per visualizzare il file con estensione wsp in SharePoint.  
  
6.  Nella barra Avvio veloce scegliere il **librerie** collegamento.  
  
7.  Nel **raccolte** , scegliere il **risorse del sito** collegamento.  
  
     Il **SPD Task Workflow** file viene elencato con altre risorse del sito.  
  
8.  Nell'elenco di file scegliere il nome del file.  
  
9. Nel **Download del File** finestra di dialogo scegliere la **salvare** pulsante per salvare il file con estensione wsp nel sistema locale.  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>Importare il File con estensione wsp in Visual Studio  
 Importare il file con estensione wsp [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando un progetto flusso di lavoro riutilizzabile. Questo progetto converte il flusso di lavoro di un flusso di lavoro riutilizzabile e dichiarativo in un flusso di lavoro di codice. Dopo aver convertito il flusso di lavoro, si utilizzerà codice per modificarne il comportamento.  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Importare un flusso di lavoro da un file con estensione wsp e modificarlo  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sulla barra dei menu, scegliere **File**, **New**, **progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.  
  
3.  Nel **modelli** riquadro, scegliere il **SharePoint 2010 flusso di lavoro riutilizzabile** modello, lasciare il nome del progetto come **WorkflowImportProject1**, quindi scegliere il **OK** pulsante.  
  
     Verrà visualizzata la personalizzazione guidata SharePoint.  
  
4.  Nel **specificare il livello di sito e di sicurezza per il debug** pagina, immettere il [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] per il secondo sito secondario di SharePoint creata in precedenza: http://*nome sistema*/SPD2.  
  
5.  Nel **qual è il livello di attendibilità per la soluzione SharePoint?** , scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **Avanti** pulsante.  
  
     Per ulteriori informazioni su creata mediante sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Nel **specificare l'origine del nuovo progetto** pagina, passare al percorso in cui è stato salvato in precedenza il file con estensione wsp nel sistema, aprire il file e quindi scegliere il **Avanti** pulsante.  
  
    > [!NOTE]  
    >  Scegliere il **fine** per importare tutti gli elementi disponibili nel file con estensione wsp.  
  
     Consente di visualizzare un elenco di flussi di lavoro riutilizzabili per l'importazione.  
  
7.  Nel **selezionare gli elementi da importare** scegliere il **SPD Task Workflow** flusso di lavoro, quindi scegliere il **fine** pulsante.  
  
     Al termine dell'operazione di importazione, un progetto denominato **WorkflowImportProject1** viene creato un flusso di lavoro denominato **SPD_Workflow_TestFT**. In questa cartella è il file di definizione del flusso di lavoro Elements.xml e il file della finestra di progettazione del flusso di lavoro (con estensione xoml). La finestra di progettazione contiene due file: il file delle regole (con estensione rules) e il file code-behind (con estensione cs o vb, a seconda del linguaggio di programmazione del progetto).  
  
8.  In **Esplora**, eliminare il **altri file importati** cartella.  
  
9. Nel file Elements.xml eliminare `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. In **Esplora**, scegliere **WorkflowImportProject1**, quindi nella barra dei menu, scegliere **progetto**, **imposta come progetto di avvio** per impostare **WorkflowImportProject1** come elemento di avvio.  
  
     Verrà visualizzato l'elenco immediatamente quando si esegue il debug del progetto.  
  
11. Poiché il **importare SharePoint 2010 flusso di lavoro riutilizzabile** modello non vengono importati i valori di proprietà di associazione per il flusso di lavoro importato, è necessario immetterli. Per eseguire questa operazione:  
  
    1.  In **Esplora**, scegliere il **SPD_Workflow_TestFT** nodo.  
  
    2.  Scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) pulsante accanto a una delle proprietà dell'elenco, ad esempio il **elenco destinazione** proprietà.  
  
    3.  Compilare i valori mancanti nella personalizzazione guidata SharePoint e quindi scegliere il **fine** pulsante.  
  
12. Scegliere il file con estensione xoml e quindi nella barra dei menu scegliere **vista**, **progettazione** per visualizzare il flusso di lavoro importato nella finestra di progettazione del flusso di lavoro.  
  
13. Nel **Windows Workflow v 3.0** nodo del **della casella degli strumenti**, eseguire una delle operazioni seguenti:  
  
    -   Aprire il menu di scelta rapida per il **codice** attività, quindi scegliere **copia**. Nella finestra di progettazione del flusso di lavoro, aprire il menu di scelta rapida per la riga sotto il **SequenceActivity1** attività, quindi scegliere **Incolla**.  
  
    -   Trascinare il **codice** attività dal **della casella degli strumenti** alla finestra di progettazione del flusso di lavoro e connetterla alla riga sottostante il **SequenceActivity1** attività.  
  
     Consente di aggiungere un'attività alla finestra di progettazione del flusso di lavoro denominato **CodeActivity1**. In questa attività si aggiungerà un'azione di codice che crea un annuncio nell'elenco di annunci quando l'utente inizia il flusso di lavoro.  
  
14. Eseguire una delle procedure seguenti:  
  
    -   Fare doppio clic su **CodeActivity1** per generare un gestore eventi e visualizzare il codice.  
  
    -   Nel **proprietà** finestra per **CodeActivity1**, impostare il valore della **ExecuteCode** proprietà **codeActivity_ExecuteCode**.  
  
15. Aggiungere quanto segue per esistente **utilizzando** o **importazioni** istruzioni:  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Sostituire `codeActivity1_ExecuteCode` con quanto segue:  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>Distribuire il progetto e associare il flusso di lavoro  
 Successivamente, eseguire WorkflowImportProject1 per distribuirlo in un sito di SharePoint e quindi associare il flusso di lavoro con l'elenco di attività per visualizzare e testare modificata, convertire del flusso di lavoro.  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Per distribuire il progetto e associare il flusso di lavoro  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] premere il tasto F5 per eseguire e distribuire il progetto di flusso di lavoro convertito.  
  
2.  Nella barra Avvio veloce scegliere il **attività** link per visualizzare l'elenco di attività.  
  
3.  Nel **strumenti elenco** scheda, scegliere il **elementi** e quindi scegliere il **nuovo elemento** pulsante.  
  
     Il **attività - nuovo elemento** verrà visualizzata la finestra di dialogo.  
  
4.  Nel **titolo** immettere **nuova attività**, quindi scegliere il **salvare** pulsante.  
  
5.  Nel **strumenti elenco** scheda, scegliere il **elenco** e quindi scegliere il **le impostazioni dell'elenco** pulsante.  
  
     Il **le impostazioni dell'elenco** verrà visualizzata la pagina.  
  
6.  Nel **autorizzazioni e gestione** , scegliere il **impostazioni flusso di lavoro** collegamento.  
  
     Il **impostazioni flusso di lavoro** verrà visualizzata la pagina.  
  
7.  Scegliere il **aggiungere un flusso di lavoro** collegamento.  
  
8.  Nel **flusso di lavoro** scegliere **WorkflowImportProject1 - SPD Workflow Test**.  
  
9. Nel **nome** immettere **SPD Workflow Test**, quindi scegliere il **OK** pulsante.  
  
10. Nella barra Avvio veloce scegliere il **attività** elenco.  
  
11. Scegliere la freccia accanto a **nuova attività**, quindi nell'elenco, scegliere **flussi di lavoro**.  
  
12. Nel **avviare un nuovo flusso di lavoro** , scegliere il collegamento per **SPD Workflow Test**, quindi scegliere il **avviare** pulsante per avviare il flusso di lavoro.  
  
    > [!NOTE]  
    >  In alternativa, è possibile associare automaticamente un flusso di lavoro con un elenco di esecuzione della procedura guidata impostazioni di flusso di lavoro e impostando il flusso di lavoro per associare automaticamente.  
  
     Si noti che vengono eseguite due azioni dal flusso di lavoro: viene visualizzato il nome dell'attività **assegnato a** colonna e un annuncio viene visualizzato nel **annunci** elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  