---
title: Valutazione dell'espressione (Visual Studio Debugging SDK) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 022a0ee21b7a58fdd69249b240490fc3c1df8361
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Valutazione dell'espressione (Visual Studio Debugging SDK)
Modalità di interruzione, l'IDE deve essere in grado di valutare le espressioni semplici che interessa diverse variabili del programma. A tale scopo, il motore di debug (DE) deve essere in grado di analizzare e valutare un'espressione che viene immesso in una delle finestre dell'IDE.  
  
 Le espressioni vengono create utilizzando il [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (metodo) e sono rappresentati da risultante [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia.  
  
 Il **IDebugExpression2** interfaccia viene implementata per la Germania e chiama il relativo **EvalAsync** per restituire un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia dell'IDE, per visualizzare il risultati della valutazione dell'espressione nell'IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) restituisce una struttura che può essere usata per inserire il valore di un'espressione in una finestra Espressioni di controllo o nella finestra variabili locali.  
  
 Gestore di debug del pacchetto o sessione di debug (SDM) chiama [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per ottenere un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il risultato della valutazione. `IDebugProperty2` dispone di metodi che restituiscono il nome, tipo e valore dell'espressione. Queste informazioni vengono visualizzate in varie finestre del debugger.  
  
## <a name="using-expression-evaluation"></a>Tramite valutazione dell'espressione  
 Per usare la valutazione dell'espressione, è necessario implementare la [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (metodo) e tutti i metodi del [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia, come illustrato nella tabella seguente.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta un'espressione in modo asincrono.|  
|[Interruzione](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina la valutazione dell'espressione asincrona.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta un'espressione in modo sincrono.|  
  
 Valutazione sincrona e asincrona è necessaria l'implementazione del [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metodo. Valutazione dell'espressione asincrona richiede l'implementazione di [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)