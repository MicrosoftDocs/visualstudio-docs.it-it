---
title: IDebugExceptionEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f2cb866c12cacc2c0fcc81c3021e7cc5af448d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Il motore di debug (DE) invia questa interfaccia al gestore di sessione di debug (SDM) quando viene generata un'eccezione nel programma attualmente in esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per i report che si è verificata un'eccezione nel programma sottoposto a debug. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Usa il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento per segnalare un'eccezione. L'evento viene inviato mediante il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando è collegato al programma sottoposto a debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugExceptionEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Ottiene informazioni dettagliate sull'eccezione che ha generato questo evento.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Ottiene una descrizione leggibile per l'eccezione che ha generato questo evento.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina se il motore di debug (DE) supporta l'opzione del passaggio di questa eccezione a un programma sottoposto a debug durante l'esecuzione riprende.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Specifica se l'eccezione deve essere passata per il programma in fase di debug quando si riprende l'esecuzione, o se l'eccezione deve essere ignorato.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Note  
 Prima di inviare l'evento, la Germania verifica se questo evento di eccezione è stato designato un'eccezione first-chance o secondo-chance da una precedente chiamata a [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Se è stata designata come un'eccezione first-chance, la `IDebugExceptionEvent2` per il SDM viene inviato l'evento. In caso contrario, la Germania assegna all'applicazione la possibilità di gestire l'eccezione. Se non viene fornito alcun gestore di eccezioni e se l'eccezione è stata designata come un'eccezione second-chance, la `IDebugExceptionEvent2` per il SDM viene inviato l'evento. In caso contrario, la Germania riprende l'esecuzione del programma e il sistema operativo o il runtime gestisce l'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)