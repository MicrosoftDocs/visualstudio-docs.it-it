---
title: 'Procedura: stampa di fogli di lavoro | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d9bd4d28afb1eca2ff07a8847081864c7af5744
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-print-worksheets"></a>Procedura: stampa di fogli di lavoro a livello di codice
  È possibile stampare qualsiasi foglio di lavoro da una cartella di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="printing-a-worksheet-in-a-document-level-customization"></a>Stampa di un foglio di lavoro in una personalizzazione a livello di documento  
  
#### <a name="to-print-a-worksheet"></a>Per stampare un foglio di lavoro  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> di `Sheet1`, richiedere due copie e visualizzare l'anteprima del documento prima della stampa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]  
  
 Il <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> metodo consente di visualizzare l'oggetto specificato nella **anteprima di stampa** finestra. Il codice seguente presuppone l'esistenza di un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> denominato `Sheet1`.  
  
#### <a name="to-preview-a-page-before-printing"></a>Per visualizzare l'anteprima di una pagina prima della stampa  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> del foglio di lavoro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]  
  
## <a name="printing-a-worksheet-in-a-vsto-add-in"></a>Stampa di un foglio di lavoro in un componente aggiuntivo VSTO  
  
#### <a name="to-print-a-worksheet"></a>Per stampare un foglio di lavoro  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> del foglio di lavoro attivo, richiedere due copie e visualizzare l'anteprima del documento prima della stampa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]  
  
 Il <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metodo consente di visualizzare l'oggetto specificato nella **anteprima di stampa** finestra.  
  
#### <a name="to-preview-a-page-before-printing"></a>Per visualizzare l'anteprima di una pagina prima della stampa  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> del foglio di lavoro attivo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: a livello di codice il controllo ortografico nei fogli di lavoro](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Elemento Host Worksheet](../vsto/worksheet-host-item.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  