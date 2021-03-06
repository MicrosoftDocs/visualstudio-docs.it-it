---
title: Comprimere intervalli o selezioni nei documenti a livello di codice
description: Si apprenderà che se si lavora con un oggetto Range o Selection, è possibile modificare la selezione in un punto di inserimento prima di inserire testo.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5d1fb41943690da5144fb06245ed7f4aa70250aa
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828644"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Procedura: Comprimere intervalli o selezioni nei documenti a livello di codice
  Se si usa un oggetto <xref:Microsoft.Office.Interop.Word.Range> o <xref:Microsoft.Office.Interop.Word.Selection> , è possibile che si voglia modificare la selezione in un punto di inserimento prima di inserire il testo, per evitare la sovrascrittura del testo esistente. Entrambi gli <xref:Microsoft.Office.Interop.Word.Range> oggetti e hanno un metodo <xref:Microsoft.Office.Interop.Word.Selection> Collapse, che usa i valori di <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> enumerazione:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> comprime la selezione nella parte iniziale. Rappresenta il valore predefinito se non viene specificato un valore di enumerazione.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> comprime la selezione nella parte finale.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Per comprimere un intervallo e inserire nuovo testo

1. Creare un oggetto <xref:Microsoft.Office.Interop.Word.Range> costituito dal primo paragrafo del documento.

    L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet46":::

    L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. Questo codice usa il documento attivo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet46":::

2. Usare il valore di enumerazione <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> per comprimere l'intervallo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet47":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet47":::

3. Inserire il nuovo testo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet48":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet48":::

4. Selezionare <xref:Microsoft.Office.Interop.Word.Range>.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet49":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet49":::

   Se si usa il valore di enumerazione <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> , il testo viene inserito all'inizio del paragrafo seguente.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet50":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet50":::

   Contrariamente a quanto potrebbe prevedersi, la nuova frase non viene inserita prima del marcatore di paragrafo perché è incluso nell'intervallo originale. Per altre informazioni, vedere Procedura: Escludere i segni di paragrafo a livello di [codice durante la creazione di intervalli.](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Per comprimere un intervallo in una personalizzazione a livello di documento

1. L'esempio seguente illustra il metodo completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet45":::

## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Per comprimere un intervallo in un componente aggiuntivo VSTO

1. L'esempio seguente illustra il metodo completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet45":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Inserire testo nei documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: Recuperare a livello di codice i caratteri iniziale e finale negli intervalli](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Procedura: Escludere i segni di paragrafo a livello di codice durante la creazione di intervalli](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: Reimpostare gli intervalli a livello di codice nei documenti di Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
