---
title: Eventi di controllo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 40e07e480a89629da919af9d6542b2879c49718f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="control-events"></a>Eventi di controllo
È necessario inviare gli eventi durante l'esecuzione controllata del programma. Tutti gli eventi vengono inviati utilizzando il [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) l'interfaccia e disporre di attributi che è necessario implementare la [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) metodo.  
  
## <a name="additional-methods"></a>Metodi aggiuntivi  
 Alcuni eventi richiedono l'implementazione di metodi aggiuntivi, come indicato di seguito:  
  
-   L'invio di [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaccia quando viene inizializzato il motore di debug (DE) è necessario implementare la [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) metodo.  
  
-   Controllo di esecuzione richiede l'implementazione di tali eventi di controllo come il [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) e[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfacce. **IDebugBreakEvent2** è obbligatorio solo per le interruzioni asincrone.  
  
-   L'esecuzione di funzioni richiede l'implementazione del [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaccia e i relativi metodi.  
  
 Gli eventi che derivano da punti di interruzione richiedono l'implementazione del [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), e [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) le interfacce, nonché il [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) metodi.  
  
 Valutazione dell'espressione asincrono è necessario implementare la [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaccia e il relativo [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md) [e GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) metodi.  
  
 Gli eventi sincroni richiedono l'implementazione di [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) metodo.  
  
 Per il motore scrivere l'output di tipo stringa, è necessario implementare la [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)