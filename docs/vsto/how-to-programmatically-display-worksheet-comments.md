---
title: 'Procedura: visualizzare a livello di codice i commenti in un foglio di lavoro | Documenti Microsoft'
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
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c43e33030cffc78bc8ee4a0665c9334bc6e8bca7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Procedura: Visualizzare commenti in un foglio di lavoro a livello di codice
  A livello di codice è possibile visualizzare e nascondere i commenti nei fogli di lavoro di Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Per visualizzare tutti i commenti in un foglio di lavoro in una personalizzazione a livello di documento  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> su **true** se si vogliono visualizzare i commenti, in caso contrario impostare su **false**. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Per visualizzare tutti i commenti in un foglio di lavoro in un componente aggiuntivo VSTO a livello di applicazione  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> su **true** se si vogliono visualizzare i commenti, in caso contrario impostare su **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: aggiungere a livello di codice ed eliminare commenti di foglio di lavoro](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  