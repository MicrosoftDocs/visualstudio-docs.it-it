---
title: 'Procedura: Contare i caratteri nei documenti a livello di codice'
description: Informazioni su come determinare il numero di caratteri in un documento usando la proprietà Count della raccolta Characters.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68ddc86183eacd7f76e39bb06e47968c0129849c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824004"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Procedura: Contare i caratteri nei documenti a livello di codice
  Il primo carattere in un documento è nella posizione del carattere 0, che rappresenta il punto di inserimento. La posizione dell'ultimo carattere è uguale al numero totale di caratteri nel documento. È possibile determinare il numero di caratteri in un documento usando la proprietà <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Characters> .

 Tutti i caratteri del documento vengono contati, inclusi gli spazi, i segni di paragrafo e altri caratteri che sono normalmente nascosti. Anche un nuovo documento vuoto restituisce un numero di un solo carattere perché contiene un segno di paragrafo.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Per visualizzare il numero di caratteri in una personalizzazione a livello di documento

1. Selezionare l'intero documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet98":::

2. Visualizzare il numero di caratteri del documento in una finestra di messaggio.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet99":::

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Per visualizzare il numero di caratteri in un componente aggiuntivo VSTO

1. Selezionare l'intero documento. L'esempio di codice seguente seleziona il documento attivo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet98":::

2. Visualizzare il numero di caratteri del documento in una finestra di messaggio.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet99":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Recuperare a livello di codice i caratteri iniziale e finale negli intervalli](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
