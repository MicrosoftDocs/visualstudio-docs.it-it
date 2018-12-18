---
title: IDebugEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aff8be869bd65def16ca0519f7c87ea82320bb99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugevent2"></a>IDebugEvent2
Questa interfaccia viene utilizzata per comunicare le informazioni di debug critici, ad esempio l'interruzione in corrispondenza di un punto di interruzione sia le informazioni non critiche, ad esempio un messaggio di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) e un fornitore di porta personalizzato implementare questa interfaccia per l'oggetto stesso come tutte le altre interfacce di eventi.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Tramite l'interfaccia argomento ID (IID) specificato per [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md), gestore di sessione di debug (SDM) chiama [QueryInterface](/cpp/atl/queryinterface) sul `IDebugEvent2` interfaccia da ottenere l'interfaccia di eventi appropriata.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Ottiene gli attributi per questo evento di debug.|  
  
## <a name="remarks"></a>Note  
 Interfacce dell'evento più specifico, ad esempio [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), non derivano dall'interfaccia IDebugEvent2 ma vengono invece implementate come un'interfaccia separata sullo stesso oggetto come `IDebugEvent2`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)