---
title: 'Procedura: a livello di programmazione comprimere intervalli o selezioni in documenti | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d4ce27e141e03b6a3cc84b00321026052893ad9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Procedura: Comprimere intervalli o selezioni in documenti a livello di codice
  Se si usa un oggetto <xref:Microsoft.Office.Interop.Word.Range> o <xref:Microsoft.Office.Interop.Word.Selection> , è possibile che si voglia modificare la selezione in un punto di inserimento prima di inserire il testo, per evitare la sovrascrittura del testo esistente. Sia il <xref:Microsoft.Office.Interop.Word.Range> e <xref:Microsoft.Office.Interop.Word.Selection> oggetti dispongono di un metodo di compressione, che usano il <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> valori di enumerazione:  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> comprime la selezione nella parte iniziale. Rappresenta il valore predefinito se non viene specificato un valore di enumerazione.  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> comprime la selezione nella parte finale.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-collapse-a-range-and-insert-new-text"></a>Per comprimere un intervallo e inserire nuovo testo  
  
1.  Creare un oggetto <xref:Microsoft.Office.Interop.Word.Range> costituito dal primo paragrafo del documento.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
     [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. Questo codice usa il documento attivo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]  
  
2.  Usare il valore di enumerazione <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> per comprimere l'intervallo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
     [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]  
  
3.  Inserire il nuovo testo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
     [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]  
  
4.  Selezionare <xref:Microsoft.Office.Interop.Word.Range>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
     [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]  
  
 Se si usa il valore di enumerazione <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> , il testo viene inserito all'inizio del paragrafo seguente.  
  
 [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
 [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]  
  
 Contrariamente a quanto potrebbe prevedersi, la nuova frase non viene inserita prima del marcatore di paragrafo perché è incluso nell'intervallo originale. Per ulteriori informazioni, vedere [come: a livello di codice escludere paragrafo segni durante la creazione di intervalli](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).  
  
## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento  
  
#### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Per comprimere un intervallo in una personalizzazione a livello di documento  
  
1.  L'esempio seguente illustra il metodo completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
#### <a name="to-collapse-a-range-in-an-vsto-add-in"></a>Per comprimere un intervallo in un componente aggiuntivo VSTO  
  
1.  L'esempio seguente illustra il metodo completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: inserire il testo nei documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Procedura: definire a livello di codice e selezionare intervalli nei documenti](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Procedura: escludere a livello di codice i segni di paragrafo durante la creazione di intervalli](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Procedura: estendere gli intervalli nei documenti](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  