---
title: IDebugModuleLoadEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModuleLoadEvent2
helpviewer_keywords:
- IDebugModuleLoadEvent2 interface
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 45136b122010ba632b31841662cd554ff7c6255d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmoduleloadevent2"></a>IDebugModuleLoadEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di sessione di debug (SDM) quando un modulo viene caricato o scaricato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugModuleLoadEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per i report che un modulo è stato caricato o scaricato. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Usa il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento al report un modulo è stato caricato o scaricato. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando è associato al programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente mostra il metodo di `IDebugModuleLoadEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|Ottiene il modulo che viene caricato o scaricato.|  
  
## <a name="remarks"></a>Note  
 Visual Studio, questo evento viene utilizzata per mantenere il **moduli** finestra aggiornata.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)