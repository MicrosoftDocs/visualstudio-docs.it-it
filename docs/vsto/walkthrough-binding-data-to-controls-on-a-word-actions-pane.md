---
title: 'Procedura dettagliata: Associazione dati a controlli in un riquadro delle azioni di Word | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d84c42e2b51d55cbbb73a7f26d6d6853ff7a3392
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-binding-data-to-controls-on-a-word-actions-pane"></a>Procedura dettagliata: associazione di dati a controlli in un riquadro delle azioni di Word
  Questa procedura dettagliata viene illustrata l'associazione di dati a controlli in un riquadro azioni in Word. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un riquadro azioni con controlli Windows Form che sono associati a dati.  
  
-   Utilizzo di una relazione master-Details per visualizzare dati nei controlli.  
  
-   Visualizzare il riquadro azioni all'apertura dell'applicazione.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Accesso a un server con il database di esempio Northwind di SQL Server.  
  
-   Autorizzazioni per leggere e scrivere nel database di SQL Server.  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 Il primo passaggio consiste nel creare un progetto Documento di Word.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto documento di Word con il nome **My Word Actions Pane**. Nella procedura guidata, selezionare **creare un nuovo documento**.  
  
     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **My Word Actions Pane** progetto **Esplora**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Aggiunta di controlli al riquadro azioni  
 Questa procedura dettagliata, è necessario un controllo riquadro azioni che contiene controlli Windows Form con associazione a dati. Aggiungere un'origine dati al progetto e quindi trascinare controlli dal **origini dati** finestra al controllo del riquadro azioni.  
  
#### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo riquadro azioni  
  
1.  Selezionare il **My Word Actions Pane** nel progetto **Esplora**.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** nella finestra di dialogo **controllo riquadro azioni**, denominarlo **ActionsControl**, quindi fare clic su **Aggiungi**.  
  
#### <a name="to-add-a-data-source-to-the-project"></a>Per aggiungere un'origine dati al progetto  
  
1.  Se la finestra **Origini dati** non è visibile, visualizzarla scegliendo **Visualizza**, **Altre finestre**e **Origini dati**dalla barra dei menu.  
  
    > [!NOTE]  
    >  Se **Mostra origini dati** non è disponibile, fare clic sul documento di Word e verificare nuovamente.  
  
2.  Fare clic su **Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati**.  
  
3.  Selezionare **Database** e quindi fare clic su **Avanti**.  
  
4.  Selezionare una connessione dati al database di SQL Server di esempio Northwind, o aggiungere una nuova connessione utilizzando il **nuova connessione** pulsante.  
  
5.  Scegliere **Avanti**.  
  
6.  Deselezionare l'opzione per salvare la connessione se è selezionata, quindi scegliere **Avanti**.  
  
7.  Espandere il **tabelle** nodo il **oggetti di Database** finestra.  
  
8.  Selezionare la casella di controllo accanto al **Suppliers** e **prodotti** tabelle.  
  
9. Scegliere **Fine**.  
  
 La procedura guidata aggiunge il **Suppliers** tabella e **prodotti** tabella il **origini dati** finestra. Aggiunge un dataset tipizzato al progetto che è visibile in **Esplora**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Per aggiungere controlli Windows Form con associazione a dati a un controllo riquadro azioni  
  
1.  Nel **origini dati** finestra, espandere il **Suppliers** tabella.  
  
2.  Fare clic sulla freccia a discesa di **nome società** nodo e selezionare **ComboBox**.  
  
3.  Trascinare **CompanyName** dal **origini dati** finestra al controllo del riquadro azioni.  
  
     Oggetto <xref:System.Windows.Forms.ComboBox> controllo viene creato sul controllo riquadro azioni. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominato `SuppliersBindingSource`, un adattatore di tabella e un <xref:System.Data.DataSet> vengono aggiunti al progetto nella barra dei componenti.  
  
4.  Selezionare `SuppliersBindingNavigator` nel **componente** barra delle applicazioni e premere CANC. Non si utilizzerà il `SuppliersBindingNavigator` in questa procedura dettagliata.  
  
    > [!NOTE]  
    >  L'eliminazione di `SuppliersBindingNavigator` non rimuove tutto il codice che è stato generato. È possibile rimuovere questo codice.  
  
5.  Spostare la casella combinata in modo da posizionarla sotto l'etichetta e la modifica di **dimensioni** proprietà **171, 21**.  
  
6.  Nel **origini dati** finestra, espandere il **prodotti** tabella figlio il **Suppliers** tabella.  
  
7.  Fare clic sulla freccia a discesa di **ProductName** nodo e selezionare **ListBox**.  
  
8.  Trascinare **ProductName** al controllo del riquadro azioni.  
  
     Oggetto <xref:System.Windows.Forms.ListBox> controllo viene creato sul controllo riquadro azioni. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominato `ProductBindingSource` e un adattatore di tabella vengono aggiunti al progetto nella barra dei componenti.  
  
9. Spostare la casella di riepilogo in modo da posizionarla sotto l'etichetta e la modifica di **dimensioni** proprietà **171, 95**.  
  
10. Trascinare un <xref:System.Windows.Forms.Button> dal **della casella degli strumenti** nel riquadro azioni di controllo e posizionarla sotto la casella di riepilogo.  
  
11. Fare doppio clic su di <xref:System.Windows.Forms.Button>, fare clic su **proprietà** nel menu di scelta rapida e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**Inserisci**|  
    |**per**|**Inserisci**|  
  
12. Ridimensionare il controllo utente per contenere i controlli.  
  
## <a name="setting-up-the-data-source"></a>Impostazione dell'origine dati  
 Per impostare l'origine dati, aggiungere codice al <xref:System.Windows.Forms.UserControl.Load> evento del controllo del riquadro azioni per riempire il controllo con i dati di <xref:System.Data.DataTable>e impostare il <xref:System.Windows.Forms.Binding.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> proprietà per ogni controllo.  
  
#### <a name="to-load-the-control-with-data"></a>Per caricare i dati nel controllo  
  
1.  Nel <xref:System.Windows.Forms.UserControl.Load> gestore dell'evento del `ActionsControl` classe, aggiungere il codice seguente.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  In c#, è necessario collegare il gestore dell'evento per il <xref:System.Windows.Forms.UserControl.Load> evento. È possibile inserire il codice nel `ActionsControl` costruttore, dopo la chiamata a `InitializeComponent`. Per ulteriori informazioni su come creare gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
#### <a name="to-set-data-binding-properties-of-the-controls"></a>Impostare le proprietà di associazione di dati dei controlli  
  
1.  Selezionare il controllo `CompanyNameComboBox`.  
  
2.  Nel **proprietà** finestra, fare clic sul pulsante a destra del **DataSource** proprietà e selezionare **suppliersBindingSource**.  
  
3.  Fare clic sul pulsante a destra del **DisplayMember** proprietà e selezionare **CompanyName**.  
  
4.  Espandere il **DataBindings** proprietà, fare clic sul pulsante a destra del **testo** proprietà e selezionare **Nessuno**.  
  
5.  Selezionare il controllo `ProductNameListBox`.  
  
6.  Nel **proprietà** finestra, fare clic sul pulsante a destra del **DataSource** proprietà e selezionare **productsBindingSource**.  
  
7.  Fare clic sul pulsante a destra del **DisplayMember** proprietà e selezionare **ProductName**.  
  
8.  Espandere il **DataBindings** proprietà, fare clic sul pulsante a destra del **SelectedValue** proprietà e selezionare **Nessuno**.  
  
## <a name="adding-a-method-to-insert-data-into-a-table"></a>Aggiunta di un metodo per inserire dati in una tabella  
 L'attività successiva consiste nel leggere i dati da controlli associati e popolare una tabella nel documento di Word. Innanzitutto, creare una routine per formattare le intestazioni della tabella e quindi aggiungere il `AddData` metodo per creare e formattare una tabella di Word.  
  
#### <a name="to-format-the-table-headings"></a>Per formattare le intestazioni della tabella  
  
1.  Nel `ActionsControl` di classi, creare un metodo per formattare le intestazioni della tabella.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
#### <a name="to-create-the-table"></a>Per creare la tabella  
  
1.  Nel `ActionsControl` classe, scrivere un metodo che verrà creata una tabella se non già esiste e aggiungere la tabella dati nel riquadro azioni.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
#### <a name="to-insert-text-into-a-word-table"></a>Per inserire testo in una tabella di Word  
  
1.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del **inserire** pulsante.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  In c#, è necessario creare un gestore eventi per il <xref:System.Windows.Forms.Control.Click> evento del pulsante.  È possibile inserire il codice nel <xref:System.Windows.Forms.UserControl.Load> gestore dell'evento del `ActionsControl` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="showing-the-actions-pane"></a>Visualizzazione del riquadro azioni  
 Nel riquadro azioni diventa visibile dopo l'aggiungono di controlli a esso.  
  
#### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni  
  
1.  In **Esplora**, fare doppio clic su **ThisDocument. vb** o **ThisDocument. cs**, quindi fare clic su **Visualizza codice** nel menu di scelta rapida.  
  
2.  Creare una nuova istanza del controllo nella parte superiore del `ThisDocument` classe in modo che risulti simile al seguente.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Aggiungere codice per il <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore dell'evento di `ThisDocument` in modo che risulti simile al seguente.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 È ora possibile testare il documento per verificare che il riquadro azioni viene visualizzato quando il documento viene aperto. Verificare la relazione master/dettaglio nei controlli nel riquadro azioni e assicurarsi che i dati vengano inseriti in una parola tabella quando la **inserire** si fa clic sul pulsante.  
  
#### <a name="to-test-your-document"></a>Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il riquadro azioni è visibile.  
  
3.  Selezionare una società nella casella combinata e verificare che gli elementi di **prodotti** elenco cambia.  
  
4.  Selezionare un prodotto, fare clic su **inserire** nel riquadro azioni e verificare che i dettagli del prodotto vengono aggiunti alla tabella di Word.  
  
5.  Inserire ulteriori prodotti da società diverse.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni fondamentali sull'associazione dati a controlli in un riquadro azioni in Word. Ecco alcune possibili attività successive:  
  
-   Associazione dati a controlli in Excel. Per ulteriori informazioni, vedere [procedura dettagliata: associazione di dati a controlli in un riquadro azioni di Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   La distribuzione del progetto. Per ulteriori informazioni, vedere [distribuisce una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)   
 [Procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  