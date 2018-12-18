---
title: 'Procedura: aggiungere a livello di codice ed eliminare commenti di foglio di lavoro | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0891524a9172c3c7adf0ca0ce55173dffb0ad19b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Procedura: Aggiungere ed eliminare commenti in un foglio di lavoro a livello di codice
  È possibile aggiungere ed eliminare commenti a livello di codice nei fogli di lavoro di Microsoft Office Excel. I commenti possono essere aggiunti solo a singole celle, non a intervalli con più celle.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="adding-and-deleting-a-comment-in-a-document-level-project"></a>Aggiunta ed eliminazione di un commento in un progetto a livello di documento  
 Gli esempi seguenti presuppongono la presenza di un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a cella singola denominato `dateComment` in un foglio di lavoro denominato `Sheet1`.  
  
#### <a name="to-add-a-new-comment-to-a-named-range"></a>Per aggiungere un nuovo commento a un intervallo denominato  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> e fornire il testo del commento. Questo codice deve essere inserito nella classe `Sheet1` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>Per eliminare un commento da un intervallo denominato  
  
1.  Verificare l'esistenza di un commento nell'intervallo ed eliminarlo. Questo codice deve essere inserito nella classe `Sheet1` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="adding-and-deleting-a-comment-in-an-vsto-add-in-project"></a>Aggiunta ed eliminazione di un commento in un progetto di componente aggiuntivo VSTO  
 Gli esempi seguenti presuppongono la presenza di un oggetto <xref:Microsoft.Office.Interop.Excel.Range> a cella singola denominato `dateComment` nel foglio di lavoro attivo.  
  
#### <a name="to-add-a-new-comment-to-an-excel-range"></a>Per aggiungere un nuovo commento a un intervallo di Excel  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> dell'oggetto <xref:Microsoft.Office.Interop.Excel.Range> e fornire il testo del commento.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
#### <a name="to-delete-a-comment-from-an-excel-range"></a>Per eliminare un commento da un intervallo di Excel  
  
1.  Verificare l'esistenza di un commento nell'intervallo ed eliminarlo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: visualizzare a livello di programmazione commenti in un foglio di lavoro](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)  
  
  