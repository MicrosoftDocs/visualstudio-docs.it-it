---
title: IDebugProcessDestroyEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessDestroyEvent2
helpviewer_keywords:
- IDebugProcessDestroyEvent2
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9122c161a0ce308c7bd2e46cb6d56c32ada85fbc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessdestroyevent2"></a>IDebugProcessDestroyEvent2
Questa interfaccia viene inviata quando un processo viene terminato, viene chiuso insolitamente o viene disconnesso da.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProcessDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) o il fornitore della porta personalizzata implementare questa interfaccia per segnalare che un processo è stato terminato. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Usa il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania o il fornitore della porta personalizzato crea e invia l'oggetto evento per segnalare la fine di un processo. La Germania, questo evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando è associato al programma in fase di debug. Il fornitore di porta personalizzato invia questo evento utilizzando il [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)