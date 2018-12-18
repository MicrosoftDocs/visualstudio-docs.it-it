---
title: 'Procedura: raggruppare a livello di codice le righe in un foglio di lavoro | Documenti Microsoft'
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
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: eeea3e917d79bd9838bbaf3ec3338129b70354ff
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Procedura: raggruppare righe in un foglio di lavoro a livello di codice
  È possibile raggruppare una o più righe intere. Per creare un gruppo in un foglio di lavoro, utilizzare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Utilizzo di un controllo NamedRange  
 Se si aggiunge un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un progetto a livello di documento in fase di progettazione, è possibile utilizzare il controllo a livello di codice, creare un gruppo. Nell'esempio seguente si presuppone che siano presenti tre <xref:Microsoft.Office.Tools.Excel.NamedRange> controlli sul foglio di lavoro: `data2001`, `data2002`, e `dataAll`. Ogni intervallo denominato fa riferimento a un'intera riga del foglio di lavoro.  
  
#### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Per creare un gruppo di controlli NamedRange in un foglio di lavoro  
  
1.  Gruppo di tre intervalli denominati chiamando il <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> metodo di ciascun intervallo. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Per separare le righe, chiamare il <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> metodo.  
  
## <a name="using-native-excel-ranges"></a>Utilizzo di intervalli di Excel nativo  
 Nel codice si presuppone che siano presenti tre intervalli di Excel denominati `data2001`, `data2002`, e `dataAll` in un foglio di lavoro.  
  
#### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Per creare un gruppo di intervalli di Excel in un foglio di lavoro  
  
1.  Gruppo di tre intervalli denominati chiamando il <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> metodo di ciascun intervallo. Nell'esempio seguente si presuppone che siano presenti tre <xref:Microsoft.Office.Interop.Excel.Range> controlli denominati `data2001`, `data2002`, e `dataAll` sul foglio di lavoro. Ogni intervallo denominato fa riferimento a un'intera riga del foglio di lavoro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Per separare le righe, chiamare il <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  