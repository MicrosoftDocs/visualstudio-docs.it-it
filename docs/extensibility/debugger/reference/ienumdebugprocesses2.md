---
title: IEnumDebugProcesses2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5fdc8d37700edb2776c905c45ddd97496228faf9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Questa interfaccia consente di enumerare i processi in esecuzione su una porta di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porta personalizzato implementa questa interfaccia per fornire un elenco di processi in esecuzione su una porta.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamate di Visual Studio [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugProcesses2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Recupera un numero specificato di processi in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Ignora un numero specificato di processi in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Ottiene il numero di processi in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Visual Studio Usa questa interfaccia per popolare il **processi** finestra.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)