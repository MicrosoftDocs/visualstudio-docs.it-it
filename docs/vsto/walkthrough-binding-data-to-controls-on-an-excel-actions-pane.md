---
title: 'Procedura dettagliata: Associazione dati a controlli in un riquadro azioni di Excel | Documenti Microsoft'
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
ms.openlocfilehash: 87d960c01d8ac28b2a148e2f48ee51a877d97c20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-binding-data-to-controls-on-an-excel-actions-pane"></a>Procedura dettagliata: associazione di dati a controlli in un riquadro delle azioni di Excel
  Questa procedura dettagliata viene illustrata l'associazione di dati a controlli in un riquadro azioni in Microsoft Office Excel. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di controlli a un foglio di lavoro.  
  
-   Creazione di un controllo riquadro azioni.  
  
-   Aggiunta di controlli Windows Form con associazione a dati a un controllo riquadro azioni.  
  
-   Visualizzazione del riquadro azioni all'apertura dell'applicazione.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un server con il database di esempio Northwind di SQL Server.  
  
-   Autorizzazioni per leggere e scrivere nel database di SQL Server.  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 Il primo passaggio consiste nella creazione di un progetto Cartella di lavoro di Excel.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **My Excel Actions Pane**. Nella procedura guidata, selezionare **creare un nuovo documento**. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione di Visual Studio e aggiunge il **My Excel Actions Pane** progetto **Esplora**.  
  
## <a name="adding-a-new-data-source-to-the-project"></a>Aggiunta di una nuova origine dati al progetto  
  
#### <a name="to-add-a-new-data-source-to-the-project"></a>Per aggiungere una nuova origine dati al progetto  
  
1.  Se la finestra **Origini dati** non è visibile, visualizzarla scegliendo **Visualizza**, **Altre finestre**e **Origini dati**dalla barra dei menu.  
  
2.  Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** e quindi fare clic su **Avanti**.  
  
4.  Selezionare una connessione dati al database di SQL Server di esempio Northwind, o aggiungere una nuova connessione utilizzando il **nuova connessione** pulsante.  
  
5.  Scegliere **Avanti**.  
  
6.  Deselezionare l'opzione per salvare la connessione se è selezionata, quindi scegliere **Avanti**.  
  
7.  Espandere il **tabelle** nodo il **oggetti di Database** finestra.  
  
8.  Selezionare la casella di controllo accanto al **Suppliers** tabella.  
  
9. Espandere il **prodotti** tabella e selezionare **ProductName**, **SupplierID**, **QuantityPerUnit**, e **UnitPrice**.  
  
10. Scegliere **Fine**.  
  
 La procedura guidata aggiunge il **Suppliers** tabella e **prodotti** tabella il **origini dati** finestra. Aggiunge un dataset tipizzato al progetto che è visibile in **Esplora**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Aggiunta di controlli al foglio di lavoro  
 Successivamente, aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo e un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo per il primo foglio di lavoro.  
  
#### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Per aggiungere un controllo NamedRange e un controllo ListObject  
  
1.  Verificare che il **Pane.xlsx di azioni di Excel personali** cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzato.  
  
2.  Nel **origini dati** finestra, espandere il **Suppliers** tabella.  
  
3.  Fare clic sulla freccia a discesa di **nome società** nodo e quindi fare clic su **NamedRange**.  
  
4.  Trascinare **nome società** dal **origini dati** finestra alla cella **A2** in `Sheet1`.  
  
     Oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `CompanyNameNamedRange` viene creato e il testo \<CompanyName > viene visualizzato nella cella **A2**. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominato `suppliersBindingSource`, un adattatore di tabella e un <xref:System.Data.DataSet> vengono aggiunti al progetto. Il controllo è associato al <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato il <xref:System.Data.DataSet> istanza.  
  
5.  Nel **origini dati** finestra, scorrere verso il basso oltre le colonne che sono sotto il **Suppliers** tabella. Nella parte inferiore dell'elenco è il **prodotti** tabella; è qui perché è un elemento figlio del **Suppliers** tabella. Selezionare questa opzione **prodotti** tabella, non quello allo stesso livello di **Suppliers** tabella e quindi fare clic sulla freccia giù visualizzata.  
  
6.  Fare clic su **ListObject** nell'elenco a discesa, quindi trascinare il **prodotti** alla cella **A6** in `Sheet1`.  
  
     Oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> controllo denominato `ProductNameListObject` viene creato nella cella **A6**. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominato `productsBindingSource` e un adattatore di tabella vengono aggiunti al progetto. Il controllo è associato al <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato il <xref:System.Data.DataSet> istanza.  
  
7.  Solo per c#, selezionare **suppliersBindingSource** sulla barra dei componenti e modificare il **modificatori** proprietà **interno** nel **proprietà** finestra.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Aggiunta di controlli al riquadro azioni  
 Successivamente, è necessario un controllo riquadro azioni che contiene una casella combinata.  
  
#### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo riquadro azioni  
  
1.  Selezionare il **My Excel Actions Pane** nel progetto **Esplora**.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** nella finestra di dialogo **controllo riquadro azioni**, denominarla **ActionsControl**, fare clic su **Aggiungi**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Per aggiungere controlli Windows Form con associazione a dati a un controllo riquadro azioni  
  
1.  Dal **controlli comuni** schede del **della casella degli strumenti**, trascinare un <xref:System.Windows.Forms.ComboBox> nel controllo riquadro azioni.  
  
2.  Modifica il **dimensioni** proprietà **171, 21**.  
  
3.  Ridimensionare il controllo utente per adattarlo alla casella combinata.  
  
## <a name="binding-the-control-on-the-actions-pane-to-data"></a>Associazione del controllo nel riquadro azioni ai dati  
 In questa sezione si imposterà l'origine dati di <xref:System.Windows.Forms.ComboBox> alla stessa origine dati come il <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nel foglio di lavoro.  
  
#### <a name="to-set-data-binding-properties-of-the-control"></a>Impostare le proprietà di associazione di dati del controllo  
  
1.  Fare doppio clic sul controllo riquadro azioni e quindi fare clic su **Visualizza codice**.  
  
2.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.UserControl.Load> evento del controllo del riquadro azioni.  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  In c#, è necessario creare un gestore eventi per il `ActionsControl`. È possibile inserire il codice nel `ActionsControl` costruttore. Per ulteriori informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="showing-the-actions-pane"></a>Visualizzazione del riquadro azioni  
 Nel riquadro azioni non è visibile finché non si aggiunge il controllo in fase di esecuzione.  
  
#### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni  
  
1.  In **Esplora**mouse ThisWorkbook. vb o ThisWorkbook. cs e quindi fare clic su **Visualizza codice**.  
  
2.  Creare una nuova istanza del controllo utente nel `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  Nel <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> gestore dell'evento di `ThisWorkbook`, aggiungere il controllo riquadro azioni.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 È ora possibile testare il documento per verificare che nel riquadro azioni viene aperto quando il documento è aperto e che i controlli hanno una relazione master/dettaglio.  
  
#### <a name="to-test-your-document"></a>Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il riquadro azioni è visibile.  
  
3.  Nella casella di riepilogo, selezionare una società. Verificare che il nome della società sia elencato nel <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo e i dettagli del prodotto sono elencati nel <xref:Microsoft.Office.Tools.Excel.ListObject> controllo.  
  
4.  Selezionare varie aziende per verificare il nome della società e i dettagli sul prodotto modificati in maniera appropriata.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Ecco alcune possibili attività successive:  
  
-   Associazione dati a controlli in Word. Per ulteriori informazioni, vedere [procedura dettagliata: associazione di dati a controlli in un riquadro azioni di Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   La distribuzione del progetto. Per ulteriori informazioni, vedere [distribuisce una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)   
 [Procedura: gestire il Layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  