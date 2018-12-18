---
title: IDebugFunctionPosition2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73097a7133de095d72a6ae22b9aff701b52ef191
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Questa interfaccia rappresenta una posizione astratta di una funzione in un documento di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare la posizione di una funzione all'interno di un documento di origine.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia è fornita come parte di un [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (in particolare, un [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) struttura) che a sua volta fa parte di [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struttura utilizzata per creare un punto di interruzione in sospeso.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugFunctionPosition2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Ottiene il nome della funzione che questa posizione è relativo.|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Ottiene l'offset dall'inizio della funzione.|  
  
## <a name="remarks"></a>Note  
 La posizione rappresentata da questa interfaccia è basata su testo, in particolare, un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)