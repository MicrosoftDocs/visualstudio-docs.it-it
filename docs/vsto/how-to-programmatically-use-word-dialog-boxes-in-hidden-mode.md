---
title: "Procedura: utilizzare a livello di codice le finestre di dialogo di Word in modalità nascosta | Documenti Microsoft"
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
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 08427d6310421135032bb3517cda1eefc1122358
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Procedura: utilizzare le finestre di dialogo di Word in modalità nascosta a livello di codice
  È possibile eseguire operazioni complesse con una chiamata al metodo richiamando le finestre di dialogo incorporate in Microsoft Office Word senza che vengano visualizzate all'utente. È possibile farlo tramite il <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metodo il <xref:Microsoft.Office.Interop.Word.Dialog> oggetto senza chiamare il <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> (metodo).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>Esempi  
 Gli esempi di codice seguente viene illustrato come utilizzare il **Imposta pagina** la finestra di dialogo in modalità nascosta per impostare le proprietà di installazione di più pagine senza input dell'utente. Negli esempi viene utilizzato un <xref:Microsoft.Office.Interop.Word.Dialog> oggetto per configurare una dimensione di pagina personalizzata. Le impostazioni specifiche per l'installazione di pagina, ad esempio il margine superiore, il margine inferiore e così via, sono disponibili come proprietà di associazione tardiva del <xref:Microsoft.Office.Interop.Word.Dialog> oggetto. Queste proprietà vengono create in modo dinamico da Word in fase di esecuzione.  
  
 Nell'esempio seguente viene illustrato come eseguire questa attività nei progetti Visual Basic in cui **Option Strict** è attiva e nei progetti Visual c# che hanno come destinazione il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In questi progetti, è possibile utilizzare le funzionalità di associazione tardiva nei compilatori Visual Basic e Visual c#. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe nel progetto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 Nell'esempio seguente viene illustrato come eseguire questa attività nei progetti Visual Basic in cui **Option Strict** si trova in. In questi progetti, è necessario usare la reflection per accedere alle proprietà di associazione tardiva. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe nel progetto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: utilizzare a livello di codice le finestre di dialogo incorporate in Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)   
 [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  