---
title: Codice contesto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a84596246ae930cdffc0265f2f2e09652661819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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