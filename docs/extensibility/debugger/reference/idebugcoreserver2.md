---
title: IDebugCoreServer2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce3e4c0c933527a5db754dcd96de97283e6e8260
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Questa interfaccia viene utilizzata per rappresentare e ottenere informazioni da un server in un computer in rete.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per rappresentare un server. Ogni istanza di Visual Studio crea un'istanza di questa interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Un fornitore di porta personalizzato riceve questa interfaccia in una chiamata a [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Un motore di debug è possibile ottenere questa interfaccia indirettamente tramite una chiamata a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (che restituisce [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), un'interfaccia derivata da `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugCoreServer2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Ottiene il nome e attributi di una macchina.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Ottiene il nome di una macchina.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Ottiene un fornitore di porta esistente in un computer.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Ottiene una porta già esistente in un computer.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Crea un enumeratore per tutte le porte in un computer.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Crea un enumeratore per tutti i fornitori di porta in un computer.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Ottiene le utilità di computer per un computer.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene anche utilizzata da Visual Studio per esplorare i processi in esecuzione nel computer della rete.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)