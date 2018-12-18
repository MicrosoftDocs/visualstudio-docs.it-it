---
title: 'Procedura: ridimensionare i controlli segnalibro | Documenti Microsoft'
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
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fc546ed1b840cc072510a49a16696a1bfc91cee7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-resize-bookmark-controls"></a>Procedura: Ridimensionare i controlli Bookmark
  Le dimensioni di un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> vengono impostate quando il controllo viene aggiunto a un documento di Microsoft Office Word. È anche possibile ridimensionare tale controllo in un secondo momento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Il ridimensionamento di un segnalibro può avvenire in tre modi:  
  
-   Aggiungere o rimuovere un testo nel controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Ogni volta che si aggiunge del testo in un segnalibro, le dimensioni del segnalibro aumentano automaticamente al fine di contenere il nuovo testo. Quando si elimina il testo, le dimensioni del segnalibro si riducono automaticamente.  
  
-   Modificare le proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> del controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Questa funzionalità è utile se si modificano le dimensioni solo di un numero limitato di caratteri.  
  
-   Ricreare il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Questa funzionalità è utile in caso di una modifica sostanziale delle dimensioni o della posizione di un segnalibro.  
  
 Nei progetti a livello di documento è possibile aggiungere controlli <xref:Microsoft.Office.Tools.Word.Bookmark> al documento nel progetto in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO è possibile aggiungere i controlli <xref:Microsoft.Office.Tools.Word.Bookmark> a qualsiasi documento aperto in fase di esecuzione. Per altre informazioni, vedere [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="changing-the-start-and-end-properties"></a>Modifica delle proprietà Start ed End  
  
#### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Per ridimensionare un segnalibro in un progetto a livello di documento in fase di progettazione  
  
1.  Selezionare il segnalibro nella finestra **Proprietà** .  
  
2.  Aumentare o ridurre il valore della proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> .  
  
3.  Aumentare o ridurre il valore della proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> .  
  
#### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>Per ridimensionare un segnalibro in un progetto a livello di documento in fase di esecuzione  
  
1.  Modificare le proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> creato in fase di esecuzione o di progettazione.  
  
     L'esempio di codice seguente aggiunge cinque caratteri all'inizio di un segnalibro denominato `SampleBookmark`. In questo codice si presuppone che prima del segnalibro siano presenti almeno cinque caratteri di testo.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     L'esempio di codice seguente aggiunge cinque caratteri alla fine dello stesso segnalibro. In questo codice si presuppone che dopo il segnalibro siano presenti almeno cinque caratteri di testo.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
#### <a name="to-resize-a-bookmark-in-an-vsto-add-in-project-at-run-time"></a>Per ridimensionare un segnalibro in un progetto di componente aggiuntivo VSTO in fase di esecuzione  
  
1.  Modificare le proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> creato in fase di esecuzione.  
  
     L'esempio di codice seguente crea un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> che contiene il testo del primo paragrafo del documento attivo, quindi rimuove cinque caratteri dall'inizio e dalla fine dell'oggetto <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreating-the-bookmark"></a>Ricreazione del segnalibro  
 È possibile ridimensionare un segnalibro in un progetto a livello di documento aggiungendo un nuovo segnalibro con lo stesso nome del segnalibro esistente, ma le cui dimensioni sono diverse.  
  
#### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Per ricreare un segnalibro in un progetto a livello di documento in fase di progettazione  
  
1.  Selezionare il testo da includere nel nuovo controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
2.  Scegliere **Segnalibro** dal menu **Inserisci**.  
  
3.  Nella finestra di dialogo **Segnalibro** selezionare il nome del segnalibro da ridimensionare e scegliere **Aggiungi**.  
  
## <a name="see-also"></a>Vedere anche  
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Procedura: ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  