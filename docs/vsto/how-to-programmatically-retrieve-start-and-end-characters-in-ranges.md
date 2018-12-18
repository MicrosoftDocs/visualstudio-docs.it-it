---
title: 'Procedura: recuperare i caratteri iniziale e finale negli intervalli a livello di codice | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a79112e80885dfd64b85a90125ea059277725d33
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Procedura: Recuperare i caratteri iniziale e finale negli intervalli a livello di codice
  Questo esempio illustra come recuperare le posizioni del carattere delle posizioni iniziale e finale di un intervallo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Per recuperare i caratteri iniziale e finale di un intervallo in una personalizzazione a livello di documento  
  
1.  Ottenere i valori delle proprietà <xref:Microsoft.Office.Interop.Word.Range.Start%2A> e <xref:Microsoft.Office.Interop.Word.Range.End%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> . L'esempio di codice seguente ottiene la posizione iniziale e finale della seconda frase nel documento. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-an-vsto-add-in"></a>Per recuperare i caratteri iniziale e finale di un intervallo usando un componente aggiuntivo VSTO  
  
1.  Ottenere i valori delle proprietà <xref:Microsoft.Office.Interop.Word.Range.Start%2A> e <xref:Microsoft.Office.Interop.Word.Range.End%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> . L'esempio di codice seguente ottiene la posizione iniziale e finale della seconda frase nel documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: definire a livello di codice e selezionare intervalli nei documenti](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: estendere gli intervalli nei documenti](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Procedura: a livello di programmazione reimpostare gli intervalli in Word documenti](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Procedura: a livello di programmazione comprimere intervalli o selezioni in documenti](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Procedura: escludere a livello di codice i segni di paragrafo durante la creazione di intervalli](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Procedura: Conteggiare i caratteri nei documenti a livello di codice](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  