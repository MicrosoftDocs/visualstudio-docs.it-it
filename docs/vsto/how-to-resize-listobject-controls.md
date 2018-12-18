---
title: 'Procedura: ridimensionare i controlli ListObject | Documenti Microsoft'
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
- ListObject control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 12a81e6bb4a0484b79ad42b8fbab77db97ea82c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-resize-listobject-controls"></a>Procedura: Ridimensionare i controlli ListObject
  Impostare la dimensione di un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> quando lo si aggiunge a una cartella di lavoro di Microsoft Office Excel; tuttavia, potrebbe essere necessario ridimensionarlo in seguito. Ad esempio, potrebbe essere necessario cambiare un elenco a due colonne in uno a tre colonne.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 È possibile ridimensionare controlli <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di progettazione oppure in fase di esecuzione in progetti a livello di documento. È possibile ridimensionare controlli <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di esecuzione in un progetto di componente aggiuntivo VSTO.  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Ridimensionamento di controlli ListObject in fase di progettazione](#designtime)  
  
-   [Ridimensionamento di controlli ListObject in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Ridimensionamento di controlli ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
 Per altre informazioni sui controlli <xref:Microsoft.Office.Tools.Excel.ListObject> , vedere [ListObject Control](../vsto/listobject-control.md).  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [la modalità di aggiunta di colonne a un oggetto elenco associato a dati in fase di esecuzione?](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Ridimensionamento di un controllo ListObject in fase di progettazione  
 Per ridimensionare un elenco, è possibile selezionare e trascinare uno dei punti di controllo oppure è possibile ridefinirne la dimensione nella finestra di dialogo **Ridimensiona elenco** .  
  
#### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Per ridimensionare un elenco usando la finestra di dialogo Ridimensiona elenco  
  
  
1.  Fare clic nella <xref:Microsoft.Office.Tools.Excel.ListObject> tabella. Il **strumenti di tabelle, progettazione** verrà visualizzata la scheda della barra multifunzione.  
  
2.  Nella sezione proprietà, fare clic su **ridimensionare tabella**.  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  Selezionare il nuovo intervallo di dati per la tabella.  
  
4.  Fare clic su **OK**.  
  
##  <a name="runtimedoclevel"></a> Ridimensionamento di un controllo ListObject in fase di esecuzione in un progetto a livello di documento  
 È possibile ridimensionare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di esecuzione usando il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . Non è possibile usare questo metodo per spostare il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in una nuova posizione nel foglio di lavoro. Le intestazioni devono rimanere nella stessa riga e il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ridimensionato deve sovrapporsi all'oggetto elenco originale. Il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ridimensionato deve contenere una riga di intestazione e almeno una riga di dati.  
  
#### <a name="to-resize-a-list-object-programmatically"></a>Per ridimensionare un oggetto elenco a livello di codice  
  
1.  Creare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> che si estende dalla cella **A1** a quella **B3** in `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  Ridimensionare l'elenco in modo da includere le celle da **A1** a **C5**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Ridimensionamento di un controllo ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile ridimensionare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in qualsiasi foglio di lavoro aperto in fase di esecuzione. Per altre informazioni su come aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro usando un componente aggiuntivo VSTO, vedere [How to: Add ListObject Controls to Worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
#### <a name="to-resize-a-list-object-programmatically"></a>Per ridimensionare un oggetto elenco a livello di codice  
  
1.  Creare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> che si estende dalla cella **A1** a quella **B3** in `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  Ridimensionare l'elenco in modo da includere le celle da **A1** a **C5**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject (controllo)](../vsto/listobject-control.md)   
 [Procedura: aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Procedura: ridimensionare i controlli Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)  
  
  