---
title: IDebugBreakpointUnboundEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointUnboundEvent2
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4e9b08c05fb9f89e0caf3f12be4337bfe3a9827
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointunboundevent2"></a>IDebugBreakpointUnboundEvent2
Questa interfaccia indica al gestore di sessione di debug (SDM) che un punto di interruzione associato è stato associato un programma caricato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia come parte del supporto per i punti di interruzione. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia (utilizza il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento quando un punto di interruzione associato è stato associato. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback fornita dal suo SDM quando è collegato al programma sottoposto a debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugBreakpointUnboundEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Ottiene il punto di interruzione è diventato non associato.|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|Ottiene il motivo che è stato dissociato il punto di interruzione.|  
  
## <a name="remarks"></a>Note  
 Quando viene scaricato un motore di debug DLL o una classe, tutti i punti di interruzione associato al codice in tale modulo deve essere dissociati dal programma sottoposto a debug. Un `IDebugBreakpointUnboundEvent2` viene inviato per ogni punto di interruzione non associato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)