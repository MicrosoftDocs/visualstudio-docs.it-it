---
title: 'Procedura: a livello di codice aggiungere commenti al testo nei documenti | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 752c79bf6bd586d19b9ec572d3cd643cdfd90e70
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Procedura: Aggiungere commenti al testo dei documenti a livello di codice
  La proprietà Comments della classe di documento aggiunge un commento a un intervallo di testo in un documento di Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'esempio seguente aggiunge un commento al primo paragrafo nel documento.  
  
### <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Per aggiungere un nuovo commento al testo in una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> della proprietà <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> e fornire un intervallo e il testo del commento. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
### <a name="to-add-a-new-comment-to-text-in-an-vsto-add-in"></a>Per aggiungere un nuovo commento al testo in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> della proprietà <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> e fornire un intervallo e il testo del commento.  
  
     L'esempio di codice seguente aggiunge un commento al documento attivo. Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Per modificare le iniziali dell'utente che Word aggiunge ai commenti, usare la proprietà <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> .  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: rimuovere a livello di codice tutti i commenti dai documenti](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Elemento host Document](../vsto/document-host-item.md)  
  
  