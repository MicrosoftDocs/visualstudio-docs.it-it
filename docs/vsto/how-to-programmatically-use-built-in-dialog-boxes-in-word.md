---
title: 'Procedura: utilizzare a livello di codice le finestre di dialogo incorporate in Word | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 80406a8048529f811cf9cbeadc8d185577a114f4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Procedura: Usare finestre di dialogo incorporate in Word a livello di codice
  Quando si lavora con Microsoft Office Word, esistono casi è necessario per visualizzare le finestre di dialogo per l'input dell'utente. Sebbene sia possibile creare la propria, è inoltre possibile adottare l'approccio dell'utilizzo di finestre di dialogo incorporate in Word, che sono esposte nel <xref:Microsoft.Office.Interop.Word.Dialogs> insieme il <xref:Microsoft.Office.Interop.Word.Application> oggetto. Ciò consente di accedere a oltre 200 delle finestre di dialogo predefinite, rappresentati come enumerazioni.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="displaying-dialog-boxes"></a>Visualizzazione di finestre di dialogo  
 Per visualizzare una finestra di dialogo, utilizzare uno dei valori del <xref:Microsoft.Office.Interop.Word.WdWordDialog> enumerazione per creare un <xref:Microsoft.Office.Interop.Word.Dialog> oggetto che rappresenta la finestra di dialogo che si desidera visualizzare. Chiamare quindi il <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metodo il <xref:Microsoft.Office.Interop.Word.Dialog> oggetto.  
  
 Esempio di codice seguente viene illustrato come visualizzare il **Apri File** la finestra di dialogo. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe nel progetto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="accessing-dialog-box-members-that-are-available-through-late-binding"></a>L'accesso ai membri di casella di dialogo che sono disponibili tramite l'associazione tardiva  
 Alcune proprietà e metodi di finestre di dialogo di Word sono disponibili solo tramite l'associazione tardiva. Nei progetti Visual Basic dove **Option Strict** è attivo, è necessario usare la reflection per accedere a questi membri. Per altre informazioni, vedere [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md).  
  
 Esempio di codice seguente viene illustrato come utilizzare il **nome** proprietà del **Apri File** progetti di Visual Basic nella finestra di dialogo dove **Option Strict** è disattivato o in Visual c# progetti di [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe nel progetto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Esempio di codice riportato di seguito viene illustrato come utilizzare la reflection per accedere il **nome** proprietà del **Apri File** progetti di Visual Basic nella finestra di dialogo dove **Option Strict** è in. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe nel progetto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: utilizzare a livello di codice le finestre di dialogo di Word in modalità nascosta](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Istruzione Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  