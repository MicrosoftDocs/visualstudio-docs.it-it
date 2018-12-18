---
title: 'Procedura: aggiornamento a livello di codice del testo di segnalibro | Documenti Microsoft'
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
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: af3252f87bd3c7d6a6c6e75ae85cea4cd75bd1e9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Procedura: aggiornare testo di segnalibro a livello di codice
  È possibile inserire testo in un segnalibro in un documento di Microsoft Office Word in modo da poter recuperare il testo in seguito o sostituire il testo in un segnalibro. Se si sviluppa una personalizzazione a livello di documento, è anche possibile aggiornare il testo in un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> associato a dati. Per ulteriori informazioni, vedere [associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'oggetto segnalibro può essere di due tipi diversi:  
  
-   Controllo host <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     I controlli <xref:Microsoft.Office.Tools.Word.Bookmark> estendono gli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> nativi permettendo il data binding e l'esposizione di eventi. Per altre informazioni sui controlli host, vedere [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
-   Oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo.  
  
     Gli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> non includono eventi né hanno funzionalità di data binding.  
  
 Quando si assegna testo a un segnalibro, il comportamento tra un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> e un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> è diverso. Per altre informazioni, vedere [Bookmark Control](../vsto/bookmark-control.md).  
  
## <a name="using-host-controls"></a>Uso di controlli host  
  
#### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Per aggiornare il contenuto dei segnalibri mediante un controllo Bookmark  
  
1.  Creare una routine che accetti un argomento `bookmark` per il nome del segnalibro e un argomento `newText` per la stringa da assegnare alla proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.  
  
    > [!NOTE]  
    >  Se si assegna testo alla proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> o <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> di un controllo <xref:Microsoft.Office.Tools.Word.Bookmark>, il segnalibro non viene eliminato.  
  
     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]  
  
2.  Assegnare il *newText* stringa per il <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> proprietà del <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]  
  
## <a name="using-word-objects"></a>Uso di oggetti di Word  
  
#### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Per aggiornare il contenuto dei segnalibri mediante un oggetto Bookmark di Word  
  
1.  Creare una routine che includa un argomento `bookmark` per il nome dell'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> e un argomento `newText` per la stringa da assegnare alla proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del segnalibro.  
  
    > [!NOTE]  
    >  Se si assegna testo a un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo di Word, il segnalibro viene eliminato.  
  
     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]  
  
2.  Assegnare il *newText* stringa per il <xref:Microsoft.Office.Interop.Word.Range.Text%2A> proprietà del segnalibro, che elimina automaticamente il segnalibro. Riaggiungere quindi il segnalibro alla raccolta <xref:Microsoft.Office.Interop.Word.Bookmarks>.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: inserire il testo nei documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Controllo Bookmark](../vsto/bookmark-control.md)  
  
  