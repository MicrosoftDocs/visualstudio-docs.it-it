---
title: IDebugBreakpointErrorEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f7cd8bdb5e8a36539807970958efda8f152e5c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Questa interfaccia indica al gestore di sessione di debug (SDM) che un punto di interruzione in sospeso non può essere associato a un programma caricato, a causa di un avviso o un errore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia come parte del supporto per i punti di interruzione. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia (utilizza il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento quando un punto di interruzione in sospeso non può essere associato al programma in fase di debug. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback fornita dal suo SDM quando è collegato al programma sottoposto a debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugBreakpointErrorEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Ottiene il [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaccia che descrive l'avviso o errore.|  
  
## <a name="remarks"></a>Note  
 Ogni volta che è associato un punto di interruzione, viene inviato un evento per il SDM. Se non è possibile associare il punto di interruzione, un `IDebugBreakpointErrorEvent2` vengono inviati; in caso contrario, un [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) viene inviato.  
  
 Ad esempio, quando non è stato possibile analizzare o valutare la condizione associata con il punto di interruzione in sospeso, viene inviato un avviso che non è possibile associare il punto di interruzione in sospeso in questo momento. Ciò può verificarsi se il codice per il punto di interruzione non è ancora caricato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)