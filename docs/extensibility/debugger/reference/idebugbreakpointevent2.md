---
title: IDebugBreakpointEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointEvent2
helpviewer_keywords:
- IDebugBreakpointEvent2 interface
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72dabc4b9477231364721535b90782a0aee6396f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointevent2"></a>IDebugBreakpointEvent2
Il motore di debug (DE) invia questa interfaccia al gestore di sessione di debug (SDM) quando si arresta un programma in un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugBreakpointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia come parte del supporto per i punti di interruzione. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia (utilizza il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento quando viene rilevato almeno un punto di interruzione nel programma. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback fornita dal suo SDM quando è collegato al programma sottoposto a debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugBreakpointEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|Crea un enumeratore per tutti i punti di interruzione viene generato in corrispondenza della posizione di codice.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)