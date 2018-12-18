---
title: 'Procedura dettagliata: Modifica del foglio di lavoro formattazione mediante controlli CheckBox | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35394b5f45e3c1e456dfcfae8f4b6db50af12147
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-changing-worksheet-formatting-using-checkbox-controls"></a>Procedura dettagliata: modifica della formattazione dei fogli di lavoro mediante i controlli CheckBox
  Questa procedura dettagliata illustra le nozioni di base dell'uso di caselle di controllo in un foglio di lavoro di Microsoft Office Excel per modificare la formattazione. Utilizzare gli strumenti di sviluppo per Office in Visual Studio per creare e aggiungere codice al progetto. Per visualizzare il risultato come un esempio completo, vedere l'esempio di controlli di Excel in [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Aggiungere testo e controlli a un foglio di lavoro.  
  
-   Formattare il testo quando si seleziona un'opzione.  
  
-   Testare il progetto.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 In questo passaggio si creerà un progetto cartella di lavoro di Excel tramite Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **formattazione in Excel**. Assicurarsi che **creare un nuovo documento** è selezionata. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione di Visual Studio e aggiunge il **formattazione in Excel** progetto **Esplora**.  
  
## <a name="adding-text-and-controls-to-the-worksheet"></a>Aggiunta di testo e controlli al foglio di lavoro  
 Questa procedura dettagliata, sono necessari tre <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controlli e del testo in un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo.  
  
#### <a name="to-add-three-check-boxes"></a>Per aggiungere tre caselle di controllo  
  
1.  Verificare che la cartella di lavoro è aperta la finestra di progettazione di Visual Studio e che `Sheet1` è aperto.  
  
2.  Dal **controlli comuni** scheda della finestra il **della casella degli strumenti**, trascinare un <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controllo o accanto alla cella **B2** in **Sheet1**.  
  
3.  Dal **vista** dal menu **proprietà** finestra.  
  
4.  Assicurarsi che **Checkbox1** è visibile nella casella di riepilogo del nome oggetto del **proprietà** finestra e modificare le proprietà seguenti:  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**per**|**Grassetto**|  
  
5.  Trascinare una seconda casella di controllo accanto a celle o **B4** e modificare le proprietà seguenti:  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**per**|**Corsivo**|  
  
6.  Trascinare una terza casella di controllo accanto a celle o **B6** e modificare le proprietà seguenti:  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**per**|**carattere di sottolineatura**|  
  
7.  Selezionare tutti i controlli casella di controllo tre tenendo premuto il tasto CTRL.  
  
8.  Nel gruppo Disponi della scheda formato Excel, fare clic su **Align**, quindi fare clic su **Allinea a sinistra**.  
  
     Le tre caselle di controllo sono allineate a sinistra, in corrispondenza della posizione del primo controllo che è selezionata.  
  
     Successivamente, verrà trascinato un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo al foglio di lavoro.  
  
    > [!NOTE]  
    >  È inoltre possibile aggiungere il <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo digitando **textFont** nel **nome** casella.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Per aggiungere testo a un controllo NamedRange  
  
1.  Dal **controlli Excel** della casella degli strumenti, trascinare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo alla cella **B9**.  
  
2.  Verificare che **$B$ 9** viene visualizzato nella casella di testo modificabile e che la cella **B9** è selezionata. In caso contrario, fare clic su cella **B9** per selezionarlo.  
  
3.  Fare clic su **OK**.  
  
4.  Cella **B9** diventerà un intervallo denominato `NamedRange1`.  
  
     Sarà presente alcuna indicazione visibile nel foglio di lavoro, ma `NamedRange1` presenti il **casella nome** (sopra il foglio di lavoro sul lato sinistro) quando la cella **B9** è selezionata.  
  
5.  Assicurarsi che **NamedRange1** è visibile nella casella di riepilogo del nome oggetto del **proprietà** finestra e modificare le proprietà seguenti:  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**textFont**|  
    |**Value2**|**Fare clic su una casella di controllo per modificare la formattazione del testo.**|  
  
 Successivamente, scrivere il codice per formattare il testo quando si seleziona un'opzione.  
  
## <a name="formatting-the-text-when-an-option-is-selected"></a>Formattazione di testo quando un'opzione è selezionata  
 In questa sezione si scriverà codice in modo che quando l'utente seleziona un'opzione di formattazione, viene modificato il formato del testo nel foglio di lavoro.  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Per modificare la formattazione quando una casella di controllo è selezionata  
  
1.  Fare doppio clic su **Sheet1**, quindi fare clic su **Visualizza codice** nel menu di scelta rapida.  
  
2.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del `applyBoldFont` casella di controllo:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del `applyItalicFont` casella di controllo:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del `applyUnderlineFont` casella di controllo:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  In c#, è necessario aggiungere gestori eventi per le caselle di controllo per il <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento, come illustrato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 È ora possibile testare la cartella di lavoro per assicurarsi che il testo è formattato correttamente quando si seleziona o deseleziona una casella di controllo.  
  
#### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Selezionare o deselezionare una casella di controllo.  
  
3.  Verificare che il testo è formattato correttamente.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base utilizzando le caselle di controllo e la formattazione del testo in fogli di lavoro di Excel. Ecco alcune possibili attività successive:  
  
-   La distribuzione del progetto. Per ulteriori informazioni, vedere [distribuisce una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Usare un pulsante per popolare una casella di testo. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzazione del testo in una casella di testo in un foglio di lavoro tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Limitazioni dei controlli Windows Forms nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  