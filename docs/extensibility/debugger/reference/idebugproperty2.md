---
title: IDebugProperty2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb0cd134d30da277ddc1f984e0cf9e57dd5e4963
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2"></a>IDebugProperty2
Questa interfaccia rappresenta una proprietà di frame dello stack, una proprietà del documento programma o un'altra proprietà. La proprietà è in genere il risultato della valutazione di un'espressione.  
  
> [!NOTE]
>  Questo utilizzo di "proprietà" non deve essere confuso con una variabile membro di una classe, che pertanto anche se un `IDebugProperty2` può rappresentare tale entità.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per rappresentare un particolare tipo di valore. Ad esempio, il valore può essere un valore numerico come risultato di valutazione di un'espressione, un contesto di memoria utilizzata per la visualizzazione di memoria o un elenco di registri e i relativi valori.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere questa interfaccia, che rappresenta il risultato di una versione di valutazione. `IDebugExpression2::EvaluateAsync` Restituisce questa interfaccia per l'invio di un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaccia SDM, che a sua volta chiama [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) per recuperare la proprietà.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) restituisce questa interfaccia per fornire il documento di script associati.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) restituisce questa interfaccia per rappresentare il valore restituito di una funzione.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) restituisce questa interfaccia per rappresentare diverse proprietà del programma, ad esempio un nome o un contesto di memoria.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) restituisce questa interfaccia per rappresentare diverse proprietà del frame dello stack, ad esempio le variabili locali.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProperty2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Compila un [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struttura che descrive una proprietà.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Imposta il valore di una proprietà da una stringa.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Imposta il valore della proprietà dal valore di un riferimento specificato.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Enumera gli elementi figlio di una proprietà.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Restituisce l'elemento padre di una proprietà.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Restituisce la proprietà che descrivono la proprietà deriva la maggior parte di una proprietà.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Restituisce i byte di memoria che compongono il valore di una proprietà.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Restituisce il contesto di memoria per un valore della proprietà.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Restituisce le dimensioni, in byte, del valore della proprietà.|  
|[getReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Restituisce un riferimento al valore di questa proprietà.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Restituisce le informazioni di una proprietà estese.|  
  
## <a name="remarks"></a>Note  
 Una proprietà, come rappresentato da un `IDebugProperty2` interfaccia, può essere considerato come un valore con un nome, un tipo e un indirizzo. In termini più generali, un `IDebugProperty2` può rappresentare qualsiasi elemento che ha una struttura gerarchica, con gli elementi padre e nodi figlio.  
  
 Una proprietà è in genere transitoria che durano solo fino a quando lo stack frame corrente, ad esempio. D'altra parte, un riferimento, come rappresentato da un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interfaccia, dura fino a quando il valore rimane in memoria.  
  
 L'IDE è possibile utilizzare il `IDebugProperty2` interfaccia per consentire agli utenti di esplorare e modificare le proprietà in fase di esecuzione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)