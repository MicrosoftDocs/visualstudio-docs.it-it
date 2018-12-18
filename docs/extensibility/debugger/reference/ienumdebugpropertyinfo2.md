---
title: IEnumDebugPropertyInfo2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2cd2e15aa02004f6fe22f08894a7f3eec4c1ea22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Questa interfaccia enumera [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare le informazioni per una particolare proprietà.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere l'interfaccia che rappresenta gli elementi figlio di una determinata proprietà. Chiamare [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) per ottenere l'interfaccia che rappresenta le proprietà di un determinato stack frame.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugPropertyInfo2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Recupera un numero specificato di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Ignora un numero specificato di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Ottiene il numero di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 In generale, una proprietà è una gerarchia di informazioni che possono includere un nome, valore, l'indirizzo e tipo, nonché le informazioni appropriate per il frame di stack o l'oggetto proprietà associata. Vedere [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) per altri dettagli.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)