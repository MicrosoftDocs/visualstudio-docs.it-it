---
title: 'Procedura dettagliata: Creazione e debug di una soluzione del flusso di lavoro di SharePoint | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 90015dce107eb15859fcb707cc265b84840ca546
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-and-debugging-a-sharepoint-workflow-solution"></a>Procedura dettagliata: creazione e debug di una soluzione flusso di lavoro SharePoint
  Questa procedura dettagliata viene illustrato come creare un modello di base del flusso di lavoro sequenziale. Il flusso di lavoro controlla una proprietà di una raccolta di documenti condivisa per determinare se un documento è stato rivisto. Se il documento è stato rivisto, il flusso di lavoro termina.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un progetto di flusso di lavoro sequenziale definizione di elenco SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Creazione di attività di flusso di lavoro.  
  
-   Gestione degli eventi di attività del flusso di lavoro.  
  
> [!NOTE]  
>  Benché questa procedura dettagliata usi un progetto flusso di lavoro sequenziale, il processo è identico per un progetto flusso di lavoro macchina a stati.  
>   
>  Inoltre, il computer potrebbe essere diversi nomi o percorsi visualizzati per alcuni utente di Visual Studio gli elementi dell'interfaccia nelle istruzioni seguenti. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="adding-properties-to-the-sharepoint-shared-documents-library"></a>Aggiunta di proprietà di SharePoint raccolta documenti condivisi  
 Per tenere traccia dello stato di revisione di documenti di **documenti condivisi** libreria, verrà creata tre nuove proprietà per i documenti condivisi nel sito di SharePoint: `Status`, `Assignee`, e `Review Comments`. È possibile definire queste proprietà nel **documenti condivisi** libreria.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Per aggiungere proprietà al condivisi di SharePoint raccolta documenti  
  
1.  Aprire un sito di SharePoint, ad esempio http://\<nome di sistema > / /SitePages/Home.aspx, in un Web browser.  
  
2.  Nella barra Avvio veloce scegliere **SharedDocuments**.  
  
3.  Scegliere **libreria** sul **Strumenti raccolta** della barra multifunzione e quindi scegliere il **Crea colonna** pulsante della barra multifunzione per creare una nuova colonna.  
  
4.  Nome della colonna **stato documento**, impostarne il tipo di **scelta (menu)**specificare tre opzioni seguenti e quindi scegliere il **OK** pulsante:  
  
    -   **Revisione necessita**  
  
    -   **Revisione completata**  
  
    -   **Modifiche richieste**  
  
5.  Creare altre due colonne e assegnare loro un nome **assegnatario** e **commenti**. Impostare il tipo di colonna assegnatario come una singola riga di testo e il tipo di colonna commenti più righe di testo.  
  
## <a name="enabling-documents-to-be-edited-without-requiring-a-check-out"></a>Abilitazione di documenti essere modificato senza necessità di estrazione  
 Risulta più semplice testare il modello di flusso di lavoro quando è possibile modificare i documenti senza estrarli. Nella procedura successiva, configurare il sito di SharePoint per consentire che.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Per abilitare i documenti essere modificato senza estrarli  
  
1.  Nella barra Avvio veloce scegliere il **documenti condivisi** collegamento.  
  
2.  Nel **Strumenti raccolta** della barra multifunzione, scegliere il **libreria** scheda e quindi scegliere il **impostazioni raccolta** pulsante per visualizzare il **impostazioni raccolta documenti** pagina.  
  
3.  Nel **impostazioni generali** , scegliere il **impostazioni controllo versioni** link per visualizzare il **impostazioni controllo versioni** pagina.  
  
4.  Verificare che l'impostazione per **obbligatoria prima della modifica dei documenti** è **n**. In caso contrario, modificarla in modo che **n** e quindi scegliere il **OK** pulsante.  
  
5.  Chiudere il browser.  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>Creazione di un progetto flusso di lavoro sequenziale di SharePoint  
 Flusso di lavoro sequenza è un set di passaggi eseguiti in ordine fino al termine dell'ultima attività. In questa procedura, viene creato un flusso di lavoro sequenza che verrà applicate all'elenco documenti condivisi. La procedura guidata del flusso di lavoro consente di associare il flusso di lavoro con la definizione del sito o la definizione di elenco e consente di determinare quando il flusso di lavoro verrà avviato.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Per creare un progetto flusso di lavoro sequenziale di SharePoint  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu, scegliere **File**, **New**, **progetto** per visualizzare il **nuovo progetto** la finestra di dialogo.  
  
3.  Espandere il **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.  
  
4.  Nel **modelli** riquadro, scegliere il **progetto SharePoint 2010** modello.  
  
5.  Nel **nome** immettere **MySharePointWorkflow** e quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzato.  
  
6.  Nel **specificare il livello di sito e di sicurezza per il debug** pagina, scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante per accettare il sito di livello e predefinito attendibile.  
  
     Questo passaggio consente di impostare il livello di attendibilità per la soluzione come soluzione farm, l'unica opzione disponibile per i progetti di flusso di lavoro. Per ulteriori informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  In **Esplora**, scegliere il nodo del progetto e quindi nella barra dei menu scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
8.  In presenza di **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
9. Nel **modelli** riquadro, scegliere il **flusso di lavoro sequenziale (solo soluzione Farm)** , modello e quindi scegliere il **Aggiungi** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzato.  
  
10. Nel **specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito (**MySharePointWorkflow - Workflow1**). Mantenere il valore a tipo di modello del flusso di lavoro predefinito, **flusso di lavoro elenco**, quindi scegliere il **Avanti** pulsante.  
  
11. Nel **si desidera che Visual Studio per associare automaticamente il flusso di lavoro in una sessione di debug?** pagina, scegliere il **Avanti** pulsante per accettare tutte le impostazioni predefinite.  
  
     Questo passaggio associa automaticamente il flusso di lavoro con la raccolta documenti condivisi.  
  
12. Nel **specificano le condizioni per l'avvio del flusso di lavoro** , mantenere selezionate nelle opzioni predefinite di **come si desidera avviare il flusso di lavoro?** sezione e scegliere il **fine** pulsante.  
  
     Questa pagina consente di specificare quando viene avviato il flusso di lavoro. Per impostazione predefinita, il flusso di lavoro si avvia quando un utente avvia manualmente in SharePoint o quando si crea un elemento a cui è associato il flusso di lavoro.  
  
## <a name="creating-workflow-activities"></a>Creazione di attività del flusso di lavoro  
 I flussi di lavoro contiene uno o più *attività* che rappresentano azioni da eseguire. Utilizzare la finestra di progettazione del flusso di lavoro per organizzare le attività per un flusso di lavoro. In questa procedura, si aggiungeranno due attività al flusso di lavoro: HandleExternalEventActivity e OnWorkFlowItemChanged. Queste attività consentono di monitorare lo stato di revisione di documenti di **documenti condivisi** elenco  
  
#### <a name="to-create-workflow-activities"></a>Per creare le attività del flusso di lavoro  
  
1.  Il flusso di lavoro deve essere visualizzato nella finestra di progettazione del flusso di lavoro. In caso contrario, aprire **Workflow1.cs** o **Workflow1. vb** in **Esplora**.  
  
2.  Nella finestra di progettazione, scegliere il **OnWorkflowActivated1** attività.  
  
3.  Nel **proprietà** finestra immettere **onWorkflowActivated** accanto al **richiama** , proprietà e quindi premere INVIO.  
  
     Verrà aperto l'Editor di codice e un metodo del gestore eventi denominato onWorkflowActivated viene aggiunto al file di codice Workflow1.  
  
4.  Tornare alla finestra di progettazione del flusso di lavoro, aprire la casella degli strumenti e quindi espandere il **Windows Workflow v 3.0** nodo.  
  
5.  Nel **Windows Workflow v 3.0** nodo del **della casella degli strumenti**, eseguire una delle seguenti procedure:  
  
    1.  Aprire il menu di scelta rapida per il **mentre** attività, quindi scegliere **copia**. Nella finestra di progettazione del flusso di lavoro, aprire il menu di scelta rapida per la riga sotto il **onWorkflowActivated1** attività, quindi scegliere **Incolla**.  
  
    2.  Trascinare il **mentre** attività dal **della casella degli strumenti** alla finestra di progettazione del flusso di lavoro e connettere l'attività per la riga sotto il **onWorkflowActivated1** attività.  
  
6.  Scegliere il **WhileActivity1** attività.  
  
7.  Nel **proprietà** finestra impostare **condizione** alla condizione di codice.  
  
8.  Espandere il **condizione** proprietà, immettere **isWorkflowPending** accanto figlio **condizione** , proprietà e quindi premere INVIO.  
  
     Verrà aperto l'Editor di codice e un metodo denominato isWorkflowPending viene aggiunto al file di codice Workflow1.  
  
9. Tornare alla finestra di progettazione del flusso di lavoro, aprire la casella degli strumenti e quindi espandere il **flusso di lavoro SharePoint** nodo.  
  
10. Nel **flusso di lavoro SharePoint** nodo del **della casella degli strumenti**, eseguire una delle seguenti procedure:  
  
    -   Aprire il menu di scelta rapida per il **OnWorkflowItemChanged** attività, quindi scegliere **copia**. Nella finestra di progettazione del flusso di lavoro, aprire il menu di scelta rapida per la riga all'interno di **whileActivity1** attività, quindi scegliere **Incolla**.  
  
    -   Trascinare il **OnWorkflowItemChanged** attività dal **della casella degli strumenti** alla finestra di progettazione del flusso di lavoro e connettere l'attività alla riga all'interno di **whileActivity1** attività.  
  
11. Scegliere il **onWorkflowItemChanged1** attività.  
  
12. Nel **proprietà** finestra, impostare le proprietà come illustrato nella tabella seguente.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Richiamato**|**onWorkflowItemChanged**|  
  
## <a name="handling-activity-events"></a>Gestione degli eventi di attività  
 Infine, controllare lo stato del documento da ogni attività. Se il documento è stato rivisto, il flusso di lavoro è terminato.  
  
#### <a name="to-handle-activity-events"></a>Per gestire gli eventi di attività  
  
1.  In Workflow1.cs o Workflow1. vb, aggiungere il campo seguente all'inizio della `Workflow1` classe. Questo campo viene utilizzato in un'attività per determinare se il flusso di lavoro è stata completata.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Aggiungere il metodo seguente alla classe `Workflow1`. Questo metodo controlla il valore di `Document Status` proprietà dell'elenco dei documenti per determinare se il documento è stato rivisto. Se il `Document Status` è impostata su `Review Complete`, quindi il `checkStatus` metodo imposta la `workflowPending` campo **false** per indicare che il flusso di lavoro è pronto essere terminato.  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  Aggiungere il codice seguente per il `onWorkflowActivated` e `onWorkflowItemChanged` metodi per chiamare il `checkStatus` metodo. Quando viene avviato il flusso di lavoro, il `onWorkflowActivated` chiamate al metodo di `checkStatus` metodo per determinare se il documento è già stato rivisto. Se non si è stato modificato, il flusso di lavoro continua. Quando il documento viene salvato, il `onWorkflowItemChanged` chiamate al metodo di `checkStatus` metodo per determinare se il documento è stato rivisto. Mentre il `workflowPending` campo è impostato su **true**, il flusso di lavoro rimane in esecuzione.  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  Aggiungere il codice seguente per il `isWorkflowPending` metodo per verificare lo stato del `workflowPending` proprietà. Ogni volta che il documento viene salvato, il **whileActivity1** attività chiama la `isWorkflowPending` metodo. Questo metodo esamina il <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> proprietà del <xref:System.Workflow.Activities.ConditionalEventArgs> oggetto per determinare se il **WhileActivity1** deve continuare o di fine attività. Se la proprietà è impostata su **true**, l'attività continua. In caso contrario, l'attività e al termine il flusso di lavoro.  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  Salvare il progetto.  
  
## <a name="testing-the-sharepoint-workflow-template"></a>Test del modello di flusso di lavoro SharePoint  
 Quando si avvia il debugger, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente di distribuire il modello di flusso di lavoro nel server SharePoint e associare il flusso di lavoro con la **documenti condivisi** elenco. Per testare il flusso di lavoro, avviare un'istanza del flusso di lavoro da un documento di **documenti condivisi** elenco.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>Per testare il modello di flusso di lavoro di SharePoint  
  
1.  In Workflow1.cs o Workflow1. vb, impostare un punto di interruzione accanto al **onWorkflowActivated** metodo.  
  
2.  Premere il tasto F5 per compilare ed eseguire la soluzione.  
  
     Viene visualizzato il sito di SharePoint.  
  
3.  Nel riquadro di spostamento in SharePoint, scegliere il **documenti condivisi** collegamento.  
  
4.  Nel **documenti condivisi** pagina, scegliere il **documenti** collegamento sul **Strumenti raccolta** scheda e quindi scegliere il **Carica documento** pulsante .  
  
5.  Nel **Carica documento** finestra di dialogo scegliere la **Sfoglia** pulsante, scegliere di qualsiasi file di documento, scegliere il **aprire** e quindi scegliere il **OK** pulsante.  
  
     Ciò consente di caricare il documento selezionato nel **documenti condivisi** elenco e avvia il flusso di lavoro.  
  
6.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], verificare che il debugger si arresta nel punto di interruzione accanto al `onWorkflowActivated` metodo.  
  
7.  Premere il tasto F5 per continuare l'esecuzione.  
  
8.  Modificare le impostazioni per il documento in questo caso, è possibile mantenere i valori predefiniti per il momento scegliendo il **salvare** pulsante.  
  
     Verrà nuovamente il **documenti condivisi** pagina del sito Web di SharePoint predefinito.  
  
9. Nel **documenti condivisi** verificare che il valore di sotto di **MySharePointWorkflow - Workflow1** colonna è impostata su **In corso**. Ciò indica che il flusso di lavoro è in corso e che il documento in attesa di revisione.  
  
10. Nel **documenti condivisi** pagina, scegliere il documento, scegliere la freccia visualizzata e quindi sceglie il **Modifica proprietà** voce di menu.  
  
11. Impostare **lo stato del documento** per **revisione completata**, quindi scegliere il **salvare** pulsante.  
  
     Verrà nuovamente il **documenti condivisi** pagina del sito Web di SharePoint predefinito.  
  
12. Nel **documenti condivisi** verificare che il valore di sotto di **documento stato** colonna è impostata su **revisione completata**. Aggiornare il **documenti condivisi** pagina e verificare che il valore di sotto di **MySharePointWorkflow - Workflow1** colonna è impostata su **completato**. Ciò indica che flusso di lavoro è terminato e che il documento è stato rivisto.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Maggiori informazioni su come creare modelli di flusso di lavoro in questi argomenti:  
  
-   Per ulteriori informazioni sulle attività del flusso di lavoro di SharePoint, vedere [attività del flusso di lavoro per SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Per ulteriori informazioni sulle attività di Windows Workflow Foundation, vedere [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Progetto SharePoint e i modelli di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  