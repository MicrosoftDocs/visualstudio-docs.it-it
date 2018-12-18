---
title: 'Procedura dettagliata: Aggiornamento di un grafico in un foglio di lavoro mediante pulsanti di opzione | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 36a83dc849260f9d58595e2f52bb422a1854b5ec
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Procedura dettagliata: aggiornamento di un grafico in un foglio di lavoro mediante i pulsanti di opzione
  Questa procedura dettagliata viene illustrato l'utilizzo di pulsanti di opzione in un foglio di lavoro di Microsoft Office Excel per consentire all'utente un modo per passare rapidamente tra le opzioni di base. In questo caso, le opzioni di modificare lo stile di un grafico.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Per visualizzare il risultato come un esempio completo, vedere l'esempio di controlli di Excel in [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di un gruppo di pulsanti di opzione a un foglio di lavoro.  
  
-   Modifica dello stile del grafico quando si seleziona un'opzione.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="adding-a-chart-to-a-worksheet"></a>Aggiunta di un grafico a un foglio di lavoro  
 È possibile creare un progetto cartella di lavoro di Excel che consente di personalizzare una cartella di lavoro esistente. In questa procedura dettagliata, verrà aggiunta di un grafico a una cartella di lavoro e quindi utilizzare questa cartella di lavoro in una nuova soluzione di Excel. L'origine dati in questa procedura dettagliata è un foglio di lavoro denominato **dati per grafico**.  
  
#### <a name="to-add-the-data"></a>Per aggiungere i dati  
  
1.  Aprire Microsoft Excel.  
  
2.  Fare doppio clic su di **Sheet3** scheda e quindi fare clic su **rinominare** nel menu di scelta rapida.  
  
3.  Rinominare la scheda in **dati per grafico**.  
  
4.  Aggiungere i seguenti dati **dati per grafico** con cella A4 l'estremità superiore sinistra angolo ed E8 nell'angolo inferiore destro.  
  
    ||Q1|Q2|Q3|T4|  
    |-|--------|--------|--------|--------|  
    |Occidentale|500|550|550|600|  
    |Orientale|600|625|675|700|  
    |settentrionale|450|470|490|510|  
    |Meridionale|800|750|775|790|  
  
 Successivamente, aggiungere un grafico al primo foglio di lavoro per visualizzare i dati.  
  
#### <a name="to-add-a-chart-in-excel"></a>Per aggiungere un grafico in Excel  
  
1.  Nel **inserire** nella scheda il **grafici** gruppo, fare clic su **colonna**e quindi fare clic su **tutti i tipi di grafico**.  
  
2.  Nel **Inserisci grafico** la finestra di dialogo, fare clic su **OK**.  
  
3.  Nel **progettazione** nella scheda il **dati** gruppo, fare clic su **selezionare dati**.  
  
4.  Nel **Seleziona origine dati** la finestra di dialogo, fare clic il **intervallo Chartdata** e cancellare le selezioni predefinite.  
  
5.  Nel **dati per grafico** foglio, selezionare l'intervallo di celle contenente i numeri, che include A4 nell'angolo superiore sinistro per E8 nell'angolo inferiore destro.  
  
6.  Nel **Seleziona origine dati** la finestra di dialogo, fare clic su **OK**.  
  
7.  Riposizionare il grafico in modo da Allinea nell'angolo superiore destro alla cella **E2**.  
  
8.  Salvare il file sull'unità C e denominarlo **ExcelChart.xlsx**.  
  
9. Uscire da Excel.  
  
## <a name="creating-a-new-project"></a>Creazione di un nuovo progetto  
 In questo passaggio si creerà un progetto cartella di lavoro di Excel sulla base di **ExcelChart** cartella di lavoro.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **My Excel Chart**. Nella procedura guidata, selezionare **copia un documento esistente**.  
  
     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Fare clic su di **Sfoglia** buttonand individuare la cartella di lavoro creata precedentemente in questa procedura dettagliata.  
  
3.  Fare clic su **OK**.  
  
     Verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione di Visual Studio e aggiunge il **grafico di Excel personali** progetto **Esplora soluzioni**.  
  
## <a name="setting-properties-of-the-chart"></a>Impostazione delle proprietà del grafico  
 Quando si crea un nuovo progetto cartella di lavoro di Excel che utilizza una cartella di lavoro, i controlli host vengono creati automaticamente per tutti gli intervalli denominati, gli oggetti elenco e grafici nella cartella di lavoro. È possibile modificare il nome del <xref:Microsoft.Office.Tools.Excel.Chart> controllo utilizzando il **proprietà** finestra.  
  
#### <a name="to-change-the-name-of-the-chart-control"></a>Per modificare il nome del controllo Chart  
  
1.  Selezionare il <xref:Microsoft.Office.Tools.Excel.Chart> nella finestra di progettazione e modificare le proprietà seguenti nella **proprietà** finestra.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## <a name="adding-controls"></a>Aggiunta di controlli  
 Questo foglio di lavoro utilizza pulsanti di opzione per consentire agli utenti di modificare rapidamente lo stile del grafico. Tuttavia, devono essere esclusivi pulsanti di opzione, quando un pulsante è selezionato, nessun altro pulsante nel gruppo può essere selezionato nello stesso momento. Questo comportamento non avviene per impostazione predefinita, quando si aggiungono più pulsanti di opzione a un foglio di lavoro.  
  
 Aggiungere questo comportamento per raggruppare i pulsanti di opzione in un controllo utente, è possibile scrivere il codice dietro il controllo utente e quindi aggiungere il controllo utente al foglio di lavoro.  
  
#### <a name="to-add-a-user-control"></a>Per aggiungere un controllo utente  
  
1.  Selezionare il **My Excel Chart** nel progetto **Esplora**.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** la finestra di dialogo, fare clic su **controllo utente**, denominare il controllo **ChartOptions** e fare clic su **Aggiungi**.  
  
#### <a name="to-add-radio-buttons-to-the-user-control"></a>Per aggiungere pulsanti di opzione nel controllo utente  
  
1.  Se il controllo utente non è visibile nella finestra di progettazione, fare doppio clic su **ChartOptions** in **Esplora**.  
  
2.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, trascinare un **pulsante di opzione** al controllo utente e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**Istogramma**|  
    |**per**|**Istogramma**|  
  
3.  Aggiungere un secondo pulsante di opzione nel controllo utente e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**barChart**|  
    |**per**|**Grafico a barre**|  
  
4.  Aggiungere un terzo pulsante di opzione nel controllo utente e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**lineChart**|  
    |**per**|**Grafico a linee**|  
  
5.  Aggiungere un quarto pulsante di opzione nel controllo utente e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**opzione areaBlockChart**|  
    |**per**|**Grafico ad area**|  
  
 Successivamente, scrivere il codice per aggiornare il grafico quando si fa clic sul pulsante di opzione.  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>Modifica il grafico stile quando un pulsante di opzione è selezionata  
 È ora possibile aggiungere il codice per modificare lo stile del grafico. A tale scopo, creare un evento pubblico nel controllo utente, aggiungere una proprietà per impostare il tipo di selezione e creare un gestore eventi per il `CheckedChanged` evento di ciascuno dei pulsanti di opzione.  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>Per creare un evento e una proprietà in un controllo utente  
  
1.  In **Esplora**, fare il controllo utente e quindi fare clic su **Visualizza codice**.  
  
2.  Aggiungere codice per il `ChartOptions` classe per creare un `SelectionChanged` evento e `Selection` proprietà.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  
  
#### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Per gestire l'evento CheckedChanged dei pulsanti di opzione  
  
1.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `areaBlockChart` e quindi generare l'evento.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  
  
2.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `barChart`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  
  
3.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `columnChart`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  
  
4.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `lineChart`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  
  
5.  In C# è necessario aggiungere gestori eventi per i pulsanti di opzione. È possibile aggiungere questo codice al costruttore `ChartOptions` dopo la chiamata a `InitializeComponent`. Per informazioni su come creare gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  
  
## <a name="adding-the-user-control-to-the-worksheet"></a>Aggiunta del controllo utente al foglio di lavoro  
 Quando si compila la soluzione, il nuovo controllo utente viene automaticamente aggiunto per il **della casella degli strumenti**. È quindi possibile trascinare il controllo di **della casella degli strumenti** al foglio di lavoro.  
  
#### <a name="to-add-the-user-control-your-worksheet"></a>Per aggiungere il controllo utente al foglio di lavoro  
  
1.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Il **ChartOptions** controllo utente viene aggiunto per il **della casella degli strumenti**.  
  
2.  In **Esplora**, fare doppio clic su **Sheet1. vb** o **Sheet1. cs**, quindi fare clic su **Visualizza finestra di progettazione**.  
  
3.  Trascinare il **ChartOptions** controllo il **della casella degli strumenti** al foglio di lavoro.  
  
     Un nuovo controllo denominato `my_Excel_Chart_ChartOptions1` viene aggiunto al progetto.  
  
4.  Modificare il nome del controllo da **ChartOptions1**.  
  
## <a name="changing-the-chart-type"></a>Modifica del tipo di grafico  
 Per modificare il tipo di grafico, è possibile creare un gestore eventi che imposta lo stile in base all'opzione selezionata nel controllo utente.  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Per modificare il tipo di grafico che viene visualizzato nel foglio di lavoro  
  
1.  Aggiungere il seguente gestore eventi alla classe `Sheet1`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  
  
2.  In c#, è necessario aggiungere un gestore eventi per il controllo utente per il <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento, come illustrato di seguito. Per informazioni su come creare gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 È ora possibile testare la cartella di lavoro per verificare che il grafico viene applicato lo stile corretto quando si seleziona un pulsante di opzione.  
  
#### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Selezionare vari pulsanti di opzione.  
  
3.  Verificare che lo stile del grafico sia modificato in base alla selezione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base dell'utilizzo di pulsanti di opzione e gli stili del grafico nei fogli di lavoro. Ecco alcune possibili attività successive:  
  
-   La distribuzione del progetto. Per ulteriori informazioni, vedere [distribuisce una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
-   Usare un pulsante per popolare una casella di testo. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzazione del testo in una casella di testo in un foglio di lavoro tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
-   Modifica della formattazione di un foglio di lavoro utilizzando le caselle di controllo. Per ulteriori informazioni, vedere [procedura dettagliata: modifica del foglio di lavoro formattazione mediante controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)  
  
  