---
title: L'eliminazione di un punto di interruzione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1667da0798bba298fdead26105178905c0b9a9e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="deleting-a-breakpoint"></a>L'eliminazione di un punto di interruzione
Di seguito viene descritto il processo quando si elimina un punto di interruzione in sospeso:  
  
## <a name="deletion-process"></a>Processo di eliminazione  
 Gestore di sessione di debug (SDM) chiama il [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) metodo per rimuovere il punto di interruzione in sospeso e i punti di interruzione associato da esso.  
  
> [!NOTE]
>  Un singolo punto di interruzione associato può essere eliminato anche da una chiamata a [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)