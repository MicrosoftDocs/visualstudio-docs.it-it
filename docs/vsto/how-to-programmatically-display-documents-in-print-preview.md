---
title: 'Procedura: visualizzare i documenti a livello di codice in fase di anteprima di stampa'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a2ab538707156826be3a31252cde16e67edff9c
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257225"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Procedura: visualizzare i documenti a livello di codice in fase di anteprima di stampa
  Se la soluzione genera un report, è possibile che si voglia far visualizzare il report all'utente in modalità Anteprima di stampa.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Procedure per le personalizzazioni a livello di documento  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Per visualizzare un documento in Anteprima di stampa chiamando il metodo PrintPreview  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> della classe <xref:Microsoft.Office.Tools.Word.Document> . Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Per visualizzare un documento in Anteprima di stampa impostando la proprietà PrintPreview  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> su **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Procedure per i componenti aggiuntivi VSTO  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Per visualizzare un documento in Anteprima di stampa chiamando il metodo PrintPreview  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole visualizzare in anteprima. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Per visualizzare un documento in Anteprima di stampa impostando la proprietà PrintPreview  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> su **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: stampare i documenti a livello di codice](../vsto/how-to-programmatically-print-documents.md)   
 [Procedura: aprire documenti esistenti](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Procedura: creazione di nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md)  
  
  