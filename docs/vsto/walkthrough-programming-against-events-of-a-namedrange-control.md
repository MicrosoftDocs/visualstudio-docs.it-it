---
title: 'Procedura dettagliata: Programmazione per eventi di un controllo NamedRange | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 623177120d58b7abd29b57d55db22b8490057bab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-programming-against-events-of-a-namedrange-control"></a>Procedura dettagliata: programmazione per eventi di un controllo NamedRange
  Questa procedura dettagliata viene illustrato come aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un foglio di lavoro di Microsoft Office Excel e programmarlo per i relativi eventi utilizzando gli strumenti di sviluppo per Office in Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un foglio di lavoro.  
  
-   Programmare <xref:Microsoft.Office.Tools.Excel.NamedRange> agli eventi di controllo.  
  
-   Testare il progetto.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 In questo passaggio si creerà un progetto cartella di lavoro di Excel in Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **eventi di intervallo denominato My**. Assicurarsi che **creare un nuovo documento** è selezionata. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione di Visual Studio e aggiunge il **My eventi di intervallo denominato** progetto **Esplora**.  
  
## <a name="adding-text-and-named-ranges-to-the-worksheet"></a>Aggiunta di testo e intervalli denominati per il foglio di lavoro  
 Poiché i controlli host vengono estese a oggetti di Office, è possibile aggiungere al documento allo stesso modo in cui aggiungere l'oggetto nativo. Ad esempio, è possibile aggiungere un Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un foglio di lavoro aprendo il **inserire** dal menu **nome**e scegliendo **Definisci**. È inoltre possibile aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo trascinandolo dal **della casella degli strumenti** nel foglio di lavoro.  
  
 In questo passaggio si aggiungeranno due controlli di intervallo denominato al foglio di lavoro utilizzando il **della casella degli strumenti**e quindi aggiungere testo al foglio di lavoro.  
  
#### <a name="to-add-a-range-to-your-worksheet"></a>Per aggiungere un intervallo al foglio di lavoro  
  
1.  Verificare che il **Events.xlsx di intervallo denominato My** cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzato.  
  
2.  Dal **controlli Excel** della casella degli strumenti, trascinare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo alla cella **A1** in `Sheet1`.  
  
     Il **Aggiungi controllo NamedRange** viene visualizzata la finestra di dialogo.  
  
3.  Verificare che **$A$ 1** viene visualizzato nella casella di testo modificabile e che la cella **A1** è selezionata. In caso contrario, fare clic su cella **A1** per selezionarlo.  
  
4.  Fare clic su **OK**.  
  
     Cella **A1** diventerà un intervallo denominato `namedRange1`. Sarà presente alcuna indicazione visibile nel foglio di lavoro, ma `namedRange1` è presente il **nome** casella (che si trova sul lato sinistro del foglio di lavoro) quando la cella **A1** è selezionata.  
  
5.  Aggiungere un altro <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo alla cella **B3**.  
  
6.  Verificare che **$B$ 3** viene visualizzato nella casella di testo modificabile e che la cella **B3** è selezionata. In caso contrario, fare clic su cella **B3** per selezionarlo.  
  
7.  Fare clic su **OK**.  
  
     Cella **B3** diventerà un intervallo denominato `namedRange2`.  
  
#### <a name="to-add-text-to-your-worksheet"></a>Per aggiungere testo al foglio di lavoro  
  
1.  Nella cella **A1**, digitare il testo seguente:  
  
     **Questo è un esempio di un controllo NamedRange.**  
  
2.  Nella cella **A3** (a sinistra del `namedRange2`), digitare il testo seguente:  
  
     **Eventi:**  
  
 Nelle sezioni seguenti, si scriverà il codice che inserisce il testo in `namedRange2` e modificare le proprietà del `namedRange2` controllo in risposta al <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, e <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> gli eventi di `namedRange1`.  
  
## <a name="adding-code-to-respond-to-the-beforedoubleclick-event"></a>Aggiungere il codice per rispondere all'evento BeforeDoubleClick  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Per inserire testo in base all'evento BeforeDoubleClick NamedRange2  
  
1.  In **Esplora**, fare doppio clic su **Sheet1. vb** o **Sheet1. cs** e selezionare **Visualizza codice**.  
  
2.  Aggiungere codice pertanto `namedRange1_BeforeDoubleClick` gestore dell'evento è simile alla seguente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  In c#, è necessario aggiungere gestori eventi per l'intervallo denominato, come illustrato nel <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento riportato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="adding-code-to-respond-to-the-change-event"></a>Aggiungere il codice per rispondere all'evento di modifica  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Per inserire il testo nel controllo namedRange2 in base all'evento di modifica  
  
1.  Aggiungere codice pertanto `NamedRange1_Change` gestore dell'evento è simile alla seguente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Poiché facendo doppio clic su una cella in un intervallo di Excel passa alla modalità di modifica, una <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> evento si verifica quando la selezione viene spostata all'esterno dell'intervallo, anche se si è verificata alcuna modifica al testo.  
  
## <a name="adding-code-to-respond-to-the-selectionchange-event"></a>Aggiungere il codice per rispondere all'evento SelectionChange  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Per inserire testo in base all'evento SelectionChange namedRange2  
  
1.  Aggiungere codice pertanto **NamedRange1_SelectionChange** gestore dell'evento è simile alla seguente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Poiché facendo doppio clic su una cella in un intervallo di Excel comporta la selezione spostare nell'intervallo, un <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> evento si verifica prima di <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> si verifica l'evento.  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 Ora è possibile testare la cartella di lavoro per verificare che il testo che descrive gli eventi di un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo viene inserito in un altro intervallo denominato quando vengono generati gli eventi.  
  
#### <a name="to-test-your-document"></a>Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Posizionare il cursore in `namedRange1`e verificare che il testo per quanto riguarda la <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> evento venga inserito e viene inserito un commento nel foglio di lavoro.  
  
3.  Fare doppio clic all'interno di `namedRange1`e verificare che il testo relativo <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> eventi viene inserita con testo in corsivo di colore rosso in `namedRange2`.  
  
4.  Fare clic all'esterno di `namedRange1` e si noti che l'evento di modifica si verifica quando si esce dalla modalità di modifica, anche se è stata apportata alcuna modifica al testo.  
  
5.  Modificare il testo all'interno di `namedRange1`.  
  
6.  Fare clic all'esterno di `namedRange1`e verificare che il testo relativo <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> eventi vengano visualizzato di colore blu in `namedRange2`.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata vengono illustrati i concetti di programmazione per eventi di un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo. Di seguito è un'attività successiva potrebbe essere:  
  
-   La distribuzione del progetto. Per ulteriori informazioni, vedere [distribuisce una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Procedura: ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Procedura: Creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  