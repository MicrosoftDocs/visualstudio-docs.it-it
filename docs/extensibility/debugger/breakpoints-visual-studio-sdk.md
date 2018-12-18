---
title: I punti di interruzione (Visual Studio SDK) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: be8f0b36ebe57041e9d36b8f606bd5bddd0601bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="breakpoints-visual-studio-sdk"></a>Punti di interruzione (Visual Studio SDK)
Esistono tre tipi di punti di interruzione: in sospeso, associazione e di errore.  
  
 **Un punto di interruzione:**  
  
-   È un'astrazione che contiene tutte le informazioni necessarie per l'associazione di un punto di interruzione per uno o più contesti di codice in uno o più programmi. Ogni volta che un programma in fase di debug causa codice per caricare il motore di debug controlla tutti i punti di interruzione in sospeso per verificare se può essere associati.  
  
     Un punto di interruzione in sospeso stesso mai associa al codice, ma piuttosto raccoglie e si dice che contiene tutti i punti di interruzione associati che genera.  
  
-   È rappresentato da un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaccia.  
  
 **Un punto di interruzione associato:**  
  
-   È un'astrazione per un punto di interruzione associata o associata a un singolo codice contesto. Ogni punto di interruzione associato viene generato in risposta a un punto di interruzione in sospeso. Un punto di interruzione in sospeso può, tuttavia, generare più di un punto di interruzione associato.  
  
     Quando il codice scaricato, un punto di interruzione associato può essere non associato e rimossi.  
  
-   È rappresentato da un [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaccia.  
  
 **Un punto di interruzione di errore:**  
  
-   È un'astrazione per la descrizione di un errore durante il tentativo di associare un punto di interruzione in sospeso per un contesto di codice. Un punto di interruzione errore descrive un errore nel percorso o nell'espressione stesso punto di interruzione. Per ulteriori informazioni, vedere [associazione dei punti di interruzione](../../extensibility/debugger/binding-breakpoints.md).  
  
     L'errore del punto di interruzione può essere un errore o un avviso.  
  
-   È rappresentato da un [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Contesto del codice](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)