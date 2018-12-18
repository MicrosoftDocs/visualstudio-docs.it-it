---
title: IDebugProgramNode2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1fd14fb79d410aa20392af42e43004f46dfec73
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Questa interfaccia rappresenta un programma che è possibile eseguire il debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un motore di debug (DE) o un fornitore di porta personalizzato implementa questa interfaccia per rappresentare un programma che è possibile eseguire il debug. Questa interfaccia viene implementata in genere sullo stesso oggetto che implementa il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia. Questa interfaccia è registrata con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] chiamando [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) per tornare a questa interfaccia. Un fornitore di porta personalizzato riceve questa interfaccia tramite una chiamata a [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Un Germania riceve questa interfaccia tramite una chiamata a [collegamento](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProgramNode2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Ottiene il nome di un programma.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Ottiene il nome del processo di hosting di un programma.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Ottiene l'identificatore di processo di sistema per il processo di hosting di un programma.|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|DEPRECATO. NON USARE.|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|DEPRECATO. NON USARE. Vedere il [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia per un approccio alternativo.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Ottiene il nome e l'identificatore della DE eseguire il programma.|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|DEPRECATO. NON USARE.|  
  
## <a name="remarks"></a>Note  
 Gestore di sessione di debug (SDM) chiama in genere [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) per ottenere questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)