---
title: Valutazione dell'espressione in modalità di interruzione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66c69d6dc3dbce328e519f6d078e0aa4a5208ca0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluation-in-break-mode"></a>Valutazione dell'espressione in modalità di interruzione
Di seguito viene descritto il processo che si verifica quando il debugger è in modalità di interruzione e deve eseguire la valutazione dell'espressione.  
  
## <a name="expression-evaluation-process"></a>Processo di valutazione di espressioni  
 Ecco i passaggi fondamentali per la valutazione di un'espressione:  
  
1.  Gestore di sessione di debug (SDM) chiama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere un'interfaccia di contesto di espressione, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Chiama quindi il SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la stringa da analizzare.  
  
3.  Se ParseText non restituisce S_OK, viene restituito il motivo dell'errore.  
  
     -in caso contrario,  
  
     Se ParseText restituisce S_OK, il SDM può quindi chiamare [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere un valore finale dall'espressione analizzata.  
  
    -   In caso di utilizzo `IDebugExpression2::EvaluateSync`, l'interfaccia di callback specificato viene utilizzato per comunicare il processo in corso della valutazione. Viene restituito il valore finale un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.  
  
    -   In caso di utilizzo `IDebugExpression2::EvaluateAsync`, l'interfaccia di callback specificato viene utilizzato per comunicare il processo in corso della valutazione. Una volta completata la valutazione, EvaluateAsync invia un [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaccia tramite il callback. Con questa interfaccia, è possibile ottenere il valore finale con [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)