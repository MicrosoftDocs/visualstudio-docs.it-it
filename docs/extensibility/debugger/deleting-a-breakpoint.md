---
title: L'eliminazione di un punto di interruzione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2bff63c243590db91ea97055943b89d73ea00308
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="deleting-a-breakpoint"></a>L'eliminazione di un punto di interruzione
Di seguito viene descritto il processo quando si elimina un punto di interruzione in sospeso:  
  
## <a name="deletion-process"></a>Processo di eliminazione  
 Gestore di sessione di debug (SDM) chiama il [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) metodo per rimuovere il punto di interruzione in sospeso e i punti di interruzione associato da esso.  
  
> [!NOTE]
>  Un singolo punto di interruzione associato può essere eliminato anche da una chiamata a [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)