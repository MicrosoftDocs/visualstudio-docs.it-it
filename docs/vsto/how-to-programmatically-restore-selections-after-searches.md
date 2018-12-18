---
title: 'Procedura: ripristinare a livello di codice le selezioni dopo le ricerche | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d1f4181a1ce9431ecbdb69a4b4f00a70f8259d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Procedura: ripristinare le selezioni dopo le ricerche a livello di codice
  Se si trova e Sostituisci testo in un documento, potrebbe essere si desidera ripristinare la selezione dell'utente originale al termine della ricerca.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Il codice della procedura di esempio utilizza due <xref:Microsoft.Office.Interop.Word.Range> oggetti. Uno archivi corrente <xref:Microsoft.Office.Interop.Word.Selection>, e quello impostato l'intero documento da utilizzare come un intervallo di ricerca.  
  
### <a name="to-restore-the-users-original-selection-after-a-search"></a>Per ripristinare la selezione dell'utente originale dopo una ricerca  
  
1.  Creare il <xref:Microsoft.Office.Interop.Word.Range> oggetti per il documento e la selezione corrente.  
  
     [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
     [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2.  Eseguire la ricerca e sostituzione.  
  
     [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
     [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3.  Selezionare l'intervallo di inizio per ripristinare la selezione dell'utente originale.  
  
     [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
     [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
 L'esempio seguente mostra il metodo completo.  
  
## <a name="example"></a>Esempio  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: cercare a livello di codice e sostituire testo nei documenti](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Procedura: impostare a livello di codice le opzioni di ricerca in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Procedura: scorrere gli elementi trovati nei documenti a livello di codice in ciclo](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  