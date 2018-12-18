---
title: 'Procedura: aggiungere nuovi fogli di lavoro alle cartelle di lavoro | Documenti Microsoft'
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
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 239d4cdba093fa81eea75e1a74906b184e6ba855
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice
  È possibile creare un foglio di lavoro a livello di codice, quindi aggiungerlo alla raccolta di fogli di lavoro nella cartella di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Per aggiungere un nuovo foglio di lavoro a una cartella di lavoro in una personalizzazione a livello di documento  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]  
  
     Il nuovo foglio di lavoro è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo e non un elemento host. Per aggiungere un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> , aggiungere il foglio di lavoro in fase di progettazione.  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Per aggiungere un nuovo foglio di lavoro a una cartella di lavoro in un componente aggiuntivo VSTO  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]  
  
     Il nuovo foglio di lavoro è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo e non un elemento host. È anche possibile generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> dall'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo. Per altre informazioni, vedere [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: eliminare a livello di codice i fogli di lavoro dalle cartelle di lavoro](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Procedura: selezionare a livello di codice i fogli di lavoro](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  