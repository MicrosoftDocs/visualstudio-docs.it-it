---
title: 'Procedura: proteggere i documenti e parti di documenti a livello di codice | Documenti Microsoft'
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
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8655a03659bd3b69e23fd155620d42df6d52386c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Procedura: Proteggere documenti e parti di documenti a livello di codice
  È possibile aggiungere protezione ai documenti di Microsoft Office Word per impedire agli utenti di apportare modifiche al documento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 È anche possibile contrassegnare determinate aree del documento come eccezioni in modo che gli utenti possano modificare solo quelle aree del documento. Ad esempio, si potrebbe voler proteggere un intero documento ad eccezione di un segnalibro particolare. È possibile aggiungere facoltativamente una password in modo che gli utenti non possano rimuovere la protezione del documento a meno che non si conosca la password.  
  
> [!NOTE]  
>  Nell'esempio seguente non viene usata la protezione con password; tuttavia, si consiglia di usare una password quando si aggiunge la protezione di documenti. Per altre informazioni, vedere Esempio di strumento di protezione dei documenti [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
 È possibile anche usare i controlli contenuto per proteggere parti di un documento. Per altre informazioni, vedere [How to: Protect Parts of Documents by Using Content Controls](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="protecting-a-document-that-is-part-of-a-document-level-customization"></a>Protezione di un documento che fa parte di una personalizzazione a livello di documento  
  
#### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Per proteggere un documento che fa parte di una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> della classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
#### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Per escludere un controllo Bookmark dalla protezione di documenti  
  
1.  Proteggere l'intero documento usando il metodo <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> .  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
2.  Escludere `Bookmark1` dalla protezione di documenti.  
  
     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]  
  
### <a name="compiling-the-code"></a>Compilazione del codice  
 Per usare questi esempi di codice, eseguirli dalla classe `ThisDocument` nel progetto. Questi esempi di codice presuppongono che nel documento in cui appare questo codice sia disponibile il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> esistente denominato `Bookmark1` .  
  
## <a name="protecting-a-document-by-using-an-vsto-add-in"></a>Protezione di un documento usando un componente aggiuntivo VSTO  
  
#### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Per proteggere un documento usando un componente aggiuntivo VSTO a livello di applicazione  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole proteggere.  
  
     L'esempio di codice seguente protegge il documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Protezione con password nei documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Procedura: consentire codice per l'esecuzione sottostante i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  