---
title: IDebugProgramHost2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b0161e2dd978b82eb5b09780a3fc07c25d15667
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Questa interfaccia fornisce informazioni di host (processo) di un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug implementa questa interfaccia per l'oggetto stesso come il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per fornire informazioni sul processo di hosting. Si tratta di un'interfaccia facoltativa.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProgram2` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProgramHost2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Ottiene il titolo, un nome descrittivo o un nome di file del processo di hosting di questo programma.|  
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Ottiene l'identificatore di processo del processo di hosting di questo programma.|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Ottiene il nome del computer che in cui è in esecuzione il processo di hosting di questo programma.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)