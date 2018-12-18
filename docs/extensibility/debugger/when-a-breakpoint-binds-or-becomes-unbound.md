---
title: Quando un punto di interruzione consente di associare o diventa non associato | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 96cd1a069535e6b03f9f2cfa541a9f2899bb77fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Quando un punto di interruzione consente di associare o diventa non associato
Quando un punto di interruzione non può essere associato al momento in cui viene eseguita una chiamata di [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) metodo, l'associazione di tempo e creare ora del punto di interruzione sono diversi.  
  
## <a name="methods-called"></a>Metodi chiamati  
 Gestore di sessione di debug (SDM) chiama i metodi seguenti:  
  
1.  [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). Restituisce il DE un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).  
  
2.  [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).  
  
3.  [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).  
  
4.  Il [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) (metodo) e restituisce S_OK. Invia il DE un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) o [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).  
  
5.  [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [IDebugBreakpointBoundEvent2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) metodi per verificare e ottenere i punti di interruzione associati.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)