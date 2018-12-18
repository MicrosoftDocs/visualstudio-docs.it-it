---
title: 'Procedura: ridimensionare i controlli NamedRange | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6d475f9140607ba0ae7415a60a9589aef11a44a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-resize-namedrange-controls"></a>Procedura: Ridimensionare i controlli NamedRange
  È possibile impostare la dimensione di un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> quando lo si aggiunge a un documento di Microsoft Office Excel; tuttavia, potrebbe essere necessario ridimensionarlo in seguito.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 È possibile ridimensionare un intervallo denominato in fase di progettazione oppure in fase di esecuzione in progetti a livello di documento. È inoltre possibile ridimensionare in fase di esecuzione intervalli denominati nei componenti aggiuntivi VSTO a livello di applicazione.  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Ridimensionamento di controlli NamedRange in fase di progettazione](#designtime)  
  
-   [Ridimensionamento di controlli NamedRange in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Ridimensionamento di controlli NamedRange in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
##  <a name="designtime"></a> Resizing NamedRange Controls at Design Time  
 È possibile ridimensionare un intervallo denominato ridefinendone le dimensioni nella finestra di dialogo **Definisci nome** .  
  
#### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Per ridimensionare un intervallo denominato tramite la finestra di dialogo Definisci nome  
  
1.  Fare clic con il pulsante destro del mouse su un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> .  
  
2.  Fare clic su **Gestisci intervalli denominati** nel menu di scelta rapida.  
  
     Viene visualizzata la finestra di dialogo **Definisci nome** .  
  
3.  Selezionare l'intervallo denominato che si intende ridimensionare.  
  
4.  Deselezionare la casella **Riferito a** .  
  
5.  Selezionare le celle che si vogliono usare per definire la dimensione dell'intervallo denominato.  
  
6.  Fare clic su **OK**.  
  
##  <a name="runtimedoclevel"></a> Resizing NamedRange Controls at Run Time in a Document-Level Project  
 Per ridimensionare a livello di codice un intervallo denominato, è possibile usare la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> .  
  
> [!NOTE]  
>  Nella finestra **Proprietà** la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> è contrassegnata come di sola lettura.  
  
#### <a name="to-resize-a-named-range-programmatically"></a>Per ridimensionare un intervallo denominato a livello di codice  
  
1.  Creare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> nella cella **A1** di `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]  
  
2.  Ridimensionare l'intervallo denominato in modo da includere la cella **B1**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> Resizing NamedRange Controls at Run Time in an VSTO Add-in project  
 È possibile ridimensionare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in qualsiasi foglio di lavoro aperto in fase di esecuzione. Per altre informazioni su come aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro usando un componente aggiuntivo VSTO, vedere [How to: Add NamedRange Controls to Worksheets](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
#### <a name="to-resize-a-named-range-programmatically"></a>Per ridimensionare un intervallo denominato a livello di codice  
  
1.  Creare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> nella cella **A1** di `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]  
  
2.  Ridimensionare l'intervallo denominato in modo da includere la cella **B1**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Procedura: ridimensionare i controlli Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Procedura: Ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)  
  
  