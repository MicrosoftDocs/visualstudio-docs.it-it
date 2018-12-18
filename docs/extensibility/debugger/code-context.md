---
title: Codice contesto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 97a4c8f8a9a710fab70760d9cb6eabb61de7a26f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="code-context"></a>Contesto del codice
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un **contesto codice**:  
  
-   Fornisce un'astrazione di una posizione nel codice come conosciuto al motore di debug (DE). Per la maggior parte delle architetture in fase di esecuzione oggi un contesto del codice può essere considerato come un indirizzo nel flusso di istruzioni del programma. Per le lingue utilizzate, in codice non può essere rappresentato da istruzioni, un contesto del codice può essere rappresentato da un altro modo.  
  
-   Descrive la posizione corrente nel flusso di esecuzione del programma sottoposto a debug.  
  
-   Esiste solo quando un programma è stata interrotta in un punto di interruzione.  
  
-   Ha un contesto di documento associato.  
  
-   Viene implementata da un [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Contesto di documento](../../extensibility/debugger/document-context.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)