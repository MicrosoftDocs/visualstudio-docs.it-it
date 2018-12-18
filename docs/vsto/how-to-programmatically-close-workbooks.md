---
title: 'Procedura: chiudere a livello di codice le cartelle di lavoro | Documenti Microsoft'
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
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 321a0e7b38a15cc40308f92b436e4f88fdbaf55d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-close-workbooks"></a>Procedura: Chiudere cartelle di lavoro a livello di codice
  È possibile chiudere la cartella di lavoro attiva o specificare una cartella di lavoro da chiudere.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="closing-the-active-workbook"></a>Chiusura della cartella di lavoro attiva  
 Esistono due procedure per chiudere la cartella di lavoro attiva: una per le personalizzazioni a livello di documento e una per i componenti aggiuntivi VSTO.  
  
#### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Per chiudere la cartella di lavoro attiva in una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> per chiudere la cartella di lavoro associata alla personalizzazione. Per usare l'esempio di codice seguente, eseguirlo nella classe `Sheet1` in un progetto a livello di documento per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]  
  
#### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Per chiudere la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> per chiudere la cartella di lavoro attiva. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="closing-a-workbook-that-you-specify-by-name"></a>Chiusura di una cartella di lavoro specificata in base al nome  
 Il modo in cui viene chiusa una cartella di lavoro specificata in base al nome è identico per i componenti aggiuntivi VSTO e per le personalizzazioni a livello di documento.  
  
#### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Per chiudere una cartella di lavoro attiva specificata in base al nome  
  
1.  Specificare il nome della cartella di lavoro come argomento per la raccolta <xref:Microsoft.Office.Interop.Excel.Workbooks> . L'esempio di codice seguente presuppone l'apertura in Excel di una cartella di lavoro il cui nome è **NewWorkbook** .  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Procedura: salvare a livello di codice le cartelle di lavoro](../vsto/how-to-programmatically-save-workbooks.md)   
 [Procedura: aprire cartelle di lavoro](../vsto/how-to-programmatically-open-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  