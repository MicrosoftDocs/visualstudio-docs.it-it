---
title: 'Procedura: estendere gli intervalli nei documenti | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68c5e2811f437a01e171e33f9802503cf4d24922
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Procedura: Estendere gli intervalli nei documenti a livello di codice
  Una volta definito un oggetto <xref:Microsoft.Office.Interop.Word.Range> in un documento di Microsoft Office Word, è possibile modificare i punti iniziale e finale usando i metodi <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> e <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . I metodi <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> e <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> accettano gli stessi due argomenti, *Unit* e *Count*. I metodi *Count* rappresenta il numero di unità da spostare, mentre l'argomento *Unit* può rappresentare uno dei seguenti valori <xref:Microsoft.Office.Interop.Word.WdUnits> :  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'esempio seguente definisce un intervallo di sette caratteri. La posizione iniziale dell'intervallo viene quindi spostata sette caratteri dopo la posizione iniziale originale. Dal momento che anche la posizione finale dell'intervallo era sette caratteri dopo la posizione iniziale, il risultato è un intervallo composto da zero caratteri. All'interno del codice, la posizione finale viene spostata sette caratteri dopo la posizione finale corrente.  
  
### <a name="to-extend-a-range"></a>Per estendere un intervallo  
  
1.  Definire un intervallo di caratteri. Per ulteriori informazioni, vedere [procedura: definire a livello di codice e selezionare intervalli nei documenti](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]  
  
2.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> per spostare la posizione iniziale dell'intervallo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]  
  
3.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> per spostare la posizione finale dell'intervallo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]  
  
## <a name="document-level-customization-code"></a>Codice di personalizzazione a livello di documento  
  
#### <a name="to-extend-a-range-in-a-document-level-customization"></a>Per estendere un intervallo in una personalizzazione a livello di documento  
  
1.  L'esempio seguente mostra il codice completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]  
  
## <a name="vsto-add-in-code"></a>Codice di componente aggiuntivo VSTO  
  
#### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Per estendere un intervallo in un componente aggiuntivo VSTO a livello di applicazione  
  
1.  L'esempio seguente illustra il codice completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: a livello di programmazione reimpostare gli intervalli in Word documenti](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Procedura: a livello di programmazione comprimere intervalli o selezioni in documenti](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Procedura: definire a livello di codice e selezionare intervalli nei documenti](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Procedura: Escludere i segni di paragrafo durante l'inserimento di intervalli a livello di codice](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  