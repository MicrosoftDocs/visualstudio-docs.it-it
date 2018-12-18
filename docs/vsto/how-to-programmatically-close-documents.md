---
title: 'Procedura: chiudere i documenti a livello di codice | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2cfe248dddfa1e176ea3ebc051863461db5dd5ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-close-documents"></a>Procedura: Chiudere documenti a livello di codice
  È possibile chiudere il documento attivo oppure specificare un documento da chiudere.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="closing-the-active-document"></a>Chiusura del documento attivo  
 Esistono due procedure per chiudere il documento attivo: una per le personalizzazioni a livello di documento e una per i componenti aggiuntivi VSTO.  
  
#### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Per chiudere il documento attivo in una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Close%2A> della classe `ThisDocument` nel progetto per chiudere il documento associato alla personalizzazione. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` .  
  
    > [!NOTE]  
    >  Questo esempio passa il valore <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parametro *SaveChanges* per chiudere il documento senza salvare le modifiche o chiedere conferma all'utente.  
  
     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]  
  
#### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Per chiudere il documento attivo in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.Close%2A> della proprietà <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> per chiudere il documento attivo. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
    > [!NOTE]  
    >  Questo esempio passa il valore <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parametro *SaveChanges* per chiudere il documento senza salvare le modifiche o chiedere conferma all'utente.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]  
  
## <a name="closing-a-document-that-you-specify-by-name"></a>Chiusura di un documento specificato in base al nome  
 Il modo in cui viene chiuso un documento specificato in base al nome è identico per i componenti aggiuntivi VSTO e le personalizzazioni a livello di documento.  
  
#### <a name="to-close-a-document-that-you-specify-by-name"></a>Per chiudere un documento specificato in base al nome  
  
1.  Specificare il nome del documento come argomento per la raccolta <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> e quindi chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.Close%2A> . L'esempio di codice seguente presuppone l'apertura in Word di un documento il cui nome è **NewDocument** .  
  
    > [!NOTE]  
    >  Questo esempio passa il valore <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parametro *SaveChanges* per chiudere il documento senza salvare le modifiche o chiedere conferma all'utente.  
  
     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aprire documenti esistenti](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Procedura: salvare i documenti a livello di codice](../vsto/how-to-programmatically-save-documents.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  