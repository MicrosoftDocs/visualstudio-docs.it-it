---
title: IDebugExpression2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cd5dcce6f81e8f61f13cc09dffb460449b0deae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpression2"></a>IDebugExpression2
Questa interfaccia rappresenta un oggetto pronto espressione analizzata per l'associazione e la valutazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un'espressione analizzata pronta per essere valutata.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) restituisce questa interfaccia. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) restituisce il [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia. Queste interfacce sono accessibili solo quando il programma in fase di debug è stato sospeso e non è disponibile un frame dello stack.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugExpression2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Questa espressione viene valutata in modo asincrono.|  
|[Interruzione](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione dell'espressione asincrona.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Questa espressione viene valutata in modo sincrono.|  
  
## <a name="remarks"></a>Note  
 Quando un programma è stata interrotta, gestore di sessione di debug (SDM) Ottiene uno stack frame dalla Germania con una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Chiama quindi il SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia. Questo evento è seguito da una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per creare il `IDebugExpression2` interfaccia che rappresenta l'espressione analizzata pronta per essere valutata.  
  
 Chiama il SDM [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per valutare l'espressione e produce un valore effettivamente.  
  
 In un'implementazione di `IDebugExpressionContext2::ParseText`, la Germania utilizza COM `CoCreateInstance` funzione per creare un'istanza di un analizzatore di espressioni e ottenere un [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaccia (vedere l'esempio nel `IDebugExpressionEvaluator` interface). Chiama quindi la Germania [analizzare](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per ottenere un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) interfaccia. Questa interfaccia viene utilizzata nell'implementazione di `IDebugExpression2::EvaluateSync` e `IDebugExpression2::EvaluateAsync` per eseguire la valutazione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)