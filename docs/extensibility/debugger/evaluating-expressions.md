---
title: La valutazione di espressioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 24cc20166bad875dcaebbd5492a7fe8317539d47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="evaluating-expressions"></a>La valutazione delle espressioni
Le espressioni vengono create dalle stringhe passate dal Auto, espressioni di controllo, controllo immediato o finestra di controllo immediato. Quando viene valutata un'espressione, viene generata una stringa stampabile che contiene il nome e il tipo di variabile o argomento e il relativo valore. Questa stringa viene visualizzata nella finestra dell'IDE corrispondente.  
  
## <a name="implementation"></a>Implementazione  
 Le espressioni vengono valutate quando un programma è stata interrotta in un punto di interruzione. L'espressione stessa è rappresentata da un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia che rappresenta un'espressione analizzata che è pronta per l'associazione e di valutazione all'interno del contesto di valutazione di espressione specificata. Lo stack frame determina il contesto di valutazione di espressioni, il motore di debug (DE) fornisce l'implementazione di [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia.  
  
 Una stringa di utente e un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia, un motore di debug (DE) è possibile ottenere un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia passando la stringa di utente per il [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodo. L'interfaccia IDebugExpression2 restituita contiene pronto per la valutazione dell'espressione analizzata.  
  
 Con il `IDebugExpression2` interfaccia, la Germania può ottenere il valore dell'espressione tramite valutazione dell'espressione sincrono o asincrono, tramite [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Questo valore, insieme a nome e il tipo della variabile o argomento, viene inviato all'IDE per la visualizzazione. Il valore, il nome e tipo sono rappresentati da un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.  
  
 Per abilitare la valutazione dell'espressione, è necessario implementare un Germania il [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfacce. Valutazione sincrona e asincrona è necessaria l'implementazione del [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)