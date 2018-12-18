---
title: IDebugProcessQueryProperties | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac071afd9f9ce7d45a05408aeec32117776832f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Questa interfaccia è implementata da un'interfaccia di estensione [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) i responsabili dell'implementazione. Consente all'implementatore ottenere informazioni sull'ambiente dei processi di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Implementare questa interfaccia per ottenere informazioni sull'ambiente di esecuzione di un processo di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProcessQueryProperties`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Query per un valore della proprietà.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Query per i valori delle proprietà.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene implementata raramente.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)