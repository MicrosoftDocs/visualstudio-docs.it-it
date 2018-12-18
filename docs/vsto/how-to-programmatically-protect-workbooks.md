---
title: 'Procedura: proteggere a livello di codice le cartelle di lavoro | Documenti Microsoft'
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
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1799366258786bafb3b24b5580ccf29be1d59927
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-protect-workbooks"></a>Procedura: proteggere cartelle di lavoro a livello di codice
  È possibile proteggere una cartella di lavoro di Microsoft Office Excel in modo che gli utenti non è possibile aggiungere o eliminare fogli di lavoro e anche rimuovere la protezione della cartella di lavoro a livello di codice. È facoltativamente possibile specificare una password, indicare se si desidera proteggere (in modo che gli utenti non è possibile spostare i fogli) la struttura e indicare se si desidera windows della cartella di lavoro protetti.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Proteggere una cartella di lavoro impedisce agli utenti di modificare le celle. Per proteggere i dati, è necessario proteggere i fogli di lavoro. Per ulteriori informazioni, vedere [come: a livello di programmazione proteggere i fogli di lavoro](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 Gli esempi di codice seguente è utilizzare una variabile per contenere una password ottenuta dall'utente.  
  
## <a name="protecting-a-workbook-that-is-part-of-a-document-level-customization"></a>Proteggere una cartella di lavoro che fa parte di una personalizzazione a livello di documento  
  
#### <a name="to-protect-a-workbook"></a>Per proteggere una cartella di lavoro  
  
1.  Chiamare il <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> (metodo) della cartella di lavoro e includere una password. Per utilizzare l'esempio di codice seguente, eseguirlo nella `ThisWorkbook` classe, non in una classe foglio.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]  
  
#### <a name="to-unprotect-a-workbook"></a>Per rimuovere la protezione di una cartella di lavoro  
  
1.  Chiamare il <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> , passando una password se necessario. Per utilizzare l'esempio di codice seguente, eseguirlo nella `ThisWorkbook` classe, non in una classe foglio.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]  
  
## <a name="protecting-a-workbook-by-using-an-application-level-add-in"></a>Protezione di una cartella di lavoro usando un componente aggiuntivo a livello di applicazione  
  
#### <a name="to-protect-a-workbook"></a>Per proteggere una cartella di lavoro  
  
1.  Chiamare il <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> (metodo) della cartella di lavoro e includere una password. Nell'esempio viene utilizzata la cartella di lavoro attiva. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]  
  
#### <a name="to-unprotect-a-workbook"></a>Per rimuovere la protezione di una cartella di lavoro  
  
1.  Chiamare il <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> (metodo) della cartella di lavoro attivo, passando una password, se necessario. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Procedura: proteggere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Procedura: nascondere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  