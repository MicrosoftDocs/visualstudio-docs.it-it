---
title: 'Procedura: a livello di codice il controllo ortografico nei documenti | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a7445b48dc936bf57a5c93426e9ffcc7f114eb32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Procedura: eseguire il controllo ortografico nei documenti a livello di codice
  Per controllare l'ortografia in un documento, utilizzare il <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metodo. Questo metodo restituisce un valore booleano che indica se il parametro fornito sia stato digitato correttamente.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Per controllare l'ortografia e Visualizza risultati in una finestra di messaggio  
  
1.  Chiamare il <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metodo e passarlo a un intervallo di testo per controllare gli errori di ortografia. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: definire a livello di codice e selezionare intervalli nei documenti](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  