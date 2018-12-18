---
title: Raggiungere un punto di interruzione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f4788f8a038a274d6d94b4edf368e30ef495665
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="hitting-a-breakpoint"></a>Raggiungere un punto di interruzione
Di seguito viene descritto il processo quando il motore di debug (DE) raggiunge un punto di interruzione durante l'esecuzione o l'esecuzione di istruzioni:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Risoluzione dei problemi relativi a un punto di interruzione Hit  
  
1.  Invia il DE un [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaccia come un' **EVENT_SYNC_STOP**.  
  
2.  Gestore di sessione di debug (SDM) chiama [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere il punto di interruzione raggiunto.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)