---
title: IDebugThreadDestroyEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThreadDestroyEvent2
helpviewer_keywords:
- IDebugThreadDestroyEvent2
ms.assetid: fca3f603-9432-457b-9ddd-8b0ec17da046
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 78017b006e755ecb5177ba06f65b81e8430bdc55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthreaddestroyevent2"></a>IDebugThreadDestroyEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di sessione di debug (SDM) quando un thread è stato eseguito fino al completamento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugThreadDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per i report che un thread è stata terminata. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Usa il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento al report in cui un thread è stata terminata. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando è associato al programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugThreadDestroyEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetExitCode](../../../extensibility/debugger/reference/idebugthreaddestroyevent2-getexitcode.md)|Ottiene il codice di uscita del thread.|  
  
## <a name="remarks"></a>Note  
 Visual Studio utilizza questo evento per aggiornare il **thread** finestra.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)