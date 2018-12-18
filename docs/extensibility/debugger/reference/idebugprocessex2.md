---
title: IDebugProcessEx2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 479206b75325c1b7e6bba0e4cc4e9b53944d73d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Questa interfaccia consente la sessione di debug manager (SDM) un processo di collegamento a o la disconnessione dal processo di notifica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porta personalizzato implementa questa interfaccia per l'oggetto stesso come il [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfaccia al fine di:  
  
-   Supportano la gestione di sessioni connesse a un processo  
  
-   Supporto della connessione automatica tra più motori di debug  
  
 Se sceglie, il fornitore della porta personalizzato può implementare questa interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
  
-   Le chiamate SDM [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProcess2` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProcessEx2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa il processo di una sessione è ora il debug del processo.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa il processo che una sessione non è più il debug del processo.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Aggiunge i nodi di programma per un elenco dei motori di debug.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia è privata tra il SDM e il processo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)