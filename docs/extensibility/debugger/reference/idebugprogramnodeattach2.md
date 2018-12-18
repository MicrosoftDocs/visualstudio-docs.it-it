---
title: IDebugProgramNodeAttach2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a83f5635dfacb638a2e76054dc5ed4e887e2a3cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Consente a un nodo di programma ricevere una notifica di un tentativo di connettersi al programma associato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata nella stessa classe che implementa il [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia per ricevere una notifica di un'operazione di collegamento e per fornire la possibilità di annullare l'operazione di collegamento.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenere questa interfaccia chiamando il `QueryInterface` metodo in un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto. Il [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo deve essere chiamato prima di [Connetti](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo per fornire il nodo programma la possibilità di interrompere il processo attach.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Collega al programma associato o rinvia il collegamento del processo di [collegamento](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia è l'alternativa preferita all'oggetto deprecato [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) metodo. Tutti i motori di debug vengono sempre caricati con il `CoCreateInstance` di funzione, vale a dire viene creata un'istanza all'esterno di spazio degli indirizzi del programma sottoposto a debug.  
  
 Se una precedente implementazione del `IDebugProgramNode2::Attach_V7` metodo semplicemente l'impostazione di `GUID` del programma sottoposto a debug, quindi solo il [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (metodo) deve essere implementato.  
  
 Se una precedente implementazione del `IDebugProgramNode2::Attach_V7` utilizzato il metodo di interfaccia di callback che è stato fornito, quindi deve essere spostato a un'implementazione di tale funzionalità il [Connetti](../../../extensibility/debugger/reference/idebugengine2-attach.md) (metodo) e `IDebugProgramNodeAttach2` non di interfaccia deve essere implementato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)