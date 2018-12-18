---
title: 'Procedura: ridimensionare i controlli all''interno delle celle del foglio di lavoro | Documenti Microsoft'
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
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 01e9dfbe244d373eaa4e66c13e02c781b32b8691
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Procedura: ridimensionare i controlli nelle celle di un foglio di lavoro
  Quando si ridimensiona le colonne o le righe in un foglio di lavoro, i controlli host contenuti nelle celle automaticamente ridimensionato per l'altezza o la larghezza della cella che è stata ridimensionata. Controlli Windows Form non si ridimensionano automaticamente per impostazione predefinita.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Se si aggiungono i controlli in fase di progettazione, è necessario impostare opzioni di posizionamento per ogni controllo.  
  
 Se si aggiunge un controllo Windows Form a livello di codice e si fornisce un argomento di intervallo, il controllo viene ridimensionato automaticamente quando si ridimensiona una cella all'interno dell'intervallo. Per altre informazioni, vedere [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="resizing-controls-at-design-time"></a>Ridimensionamento di controlli in fase di progettazione  
  
#### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Per impostare i controlli ridimensionati con le celle in fase di progettazione  
  
1.  Dal **della casella degli strumenti**, trascinare un controllo Windows Form a un foglio di lavoro.  
  
2.  Il pulsante destro del controllo e quindi fare clic su **formato controllo**.  
  
3.  Nel **formato controllo** la finestra di dialogo, fare clic su di **proprietà** scheda.  
  
4.  In **oggetto posizionamento**, selezionare il **spostare e ridimensionare con le celle** opzione e quindi fare clic su **OK**.  
  
     Quando si ridimensiona la cella che contiene il controllo, il controllo viene ridimensionato per adattarsi alla cella.  
  
## <a name="resizing-controls-at-run-time"></a>Ridimensionamento di controlli in fase di esecuzione  
 Se aggiunge un controllo Windows Form in fase di esecuzione e passare un <xref:Microsoft.Office.Interop.Excel.Range> come percorso per il controllo, il controllo viene ridimensionato automaticamente quando la cella di foglio di lavoro che contiene l'intervallo viene ridimensionata.  
  
#### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Per impostare i controlli ridimensionati con le celle in fase di esecuzione  
  
1.  Aggiungere un controllo all'intervallo A1.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     Quando si ridimensiona la cella che contiene il controllo, il controllo viene ridimensionato per adattarsi alla cella.  
  
## <a name="resetting-control-placement"></a>Reimpostare il posizionamento dei controlli  
 È possibile reimpostare la posizione e il ridimensionamento del controllo impostando il `Placement` proprietà su uno dei seguenti <xref:Microsoft.Office.Interop.Excel.XlPlacement> valori:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Per modificare il comportamento di un controllo in modo che non ridimensionare o spostare la cella  
  
1.  Chiamare la proprietà di posizionamento del controllo e impostare il valore su <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procedura: nascondere i controlli nei fogli di lavoro durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitazioni dei controlli Windows Forms nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  