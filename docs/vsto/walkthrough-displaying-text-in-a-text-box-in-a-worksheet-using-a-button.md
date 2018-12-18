---
title: 'Procedura dettagliata: Visualizzazione di testo in una casella di testo in un foglio di lavoro tramite un pulsante | Documenti Microsoft'
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
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b88940aa1329bc330e5d8bb7d114c21fac3dacb
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Procedura dettagliata: visualizzazione di testo in una casella di testo di un foglio di lavoro tramite un pulsante
  Questa procedura dettagliata illustra le nozioni di base dell'uso di pulsanti e caselle di testo in fogli di lavoro di Microsoft Office Excel e come creare progetti di Excel con strumenti di sviluppo per Office in Visual Studio. Per visualizzare il risultato come un esempio completo, vedere l'esempio di controlli di Excel in [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Aggiungere controlli a un foglio di lavoro.  
  
-   Popolare una casella di testo quando viene premuto un pulsante.  
  
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
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **My Button Excel**. Assicurarsi che **creare un nuovo documento** è selezionata. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione di Visual Studio e aggiunge il **My Button Excel** progetto **Esplora**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Aggiunta di controlli al foglio di lavoro  
 Questa procedura dettagliata, è necessario un pulsante e una casella di testo il primo foglio di lavoro.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Per aggiungere un pulsante e una casella di testo  
  
1.  Verificare che il **Button.xlsx Excel My** cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzato.  
  
2.  Dal **controlli comuni** della casella degli strumenti, trascinare un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> a `Sheet1`.  
  
3.  Dal **vista** dal menu **finestra proprietà**.  
  
4.  Assicurarsi che **TextBox1** è visibile nel **proprietà** casella di riepilogo a discesa finestra e modificare il **nome** proprietà della casella di testo per **displayText**.  
  
5.  Trascinare un **pulsante** sul controllo `Sheet1` e modificare le proprietà seguenti:  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**Name**|**insertText**|  
    |**per**|**Inserire il testo**|  
  
 Ora di scrivere il codice da eseguire quando si fa clic sul pulsante.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Popolare la casella di testo quando si fa clic sul pulsante  
 Ogni volta che l'utente fa clic sul pulsante, **Hello World!** viene aggiunto alla casella di testo.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Per scrivere nella casella di testo quando si fa clic sul pulsante  
  
1.  In **Esplora**, fare doppio clic su **Sheet1**, quindi fare clic su **Visualizza codice** nel menu di scelta rapida.  
  
2.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del pulsante:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  In c#, è necessario aggiungere un gestore eventi per il <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento, come illustrato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 È ora possibile testare la cartella di lavoro per assicurarsi che il messaggio **Hello World!** Quando si fa clic sul pulsante, viene visualizzato nella casella di testo.  
  
#### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Fare clic sul pulsante.  
  
3.  Verificare che **Hello World!** viene visualizzato nella casella di testo.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base dell'utilizzo di pulsanti e caselle di testo in fogli di lavoro di Excel. Ecco alcune possibili attività successive:  
  
-   La distribuzione del progetto. Per ulteriori informazioni, vedere [distribuisce una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
-   Utilizzando le caselle di controllo per modificare la formattazione. Per ulteriori informazioni, vedere [procedura dettagliata: modifica del foglio di lavoro formattazione mediante controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)   
 [Limitazioni dei controlli Windows Forms nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  