---
title: L'analizzatore di espressioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8dd2cc4409dbdb7650454715e133fd76dda5b780
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator"></a>Analizzatore di espressioni
Analizzatori di espressioni (Java EE) esaminare la sintassi di una lingua per analizzare e valutare variabili ed espressioni in fase di esecuzione, di modo che possano essere visualizzati dall'utente quando l'ambiente IDE è in modalità di interruzione.  
  
## <a name="using-expression-evaluators"></a>Usando gli analizzatori di espressioni  
 Le espressioni vengono create utilizzando il [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (metodo), come indicato di seguito:  
  
1.  Il motore di debug (DE) implementa il [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia.  
  
2.  Ottiene il pacchetto di debug un `IDebugExpressionContext2` dell'oggetto da un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia e quindi chiama il `IDebugStackFrame2::ParseText` metodo in modo da ottenere un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto.  
  
3.  Le chiamate di pacchetto di debug di [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metodo o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metodo per ottenere il valore dell'espressione. `IDebugExpression2::EvaluateAsync` viene chiamato dalla finestra di comando/controllo immediato. Tutti gli altri componenti dell'interfaccia utente chiamano `IDebugExpression2::EvaluateSync`.  
  
4.  Il risultato della valutazione dell'espressione è un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che contiene nome, tipo e il valore del risultato della valutazione dell'espressione.  
  
 Durante la valutazione dell'espressione, l'analizzatore di Espressioni richiede informazioni dal componente di provider di simboli. Il provider di simboli fornisce le informazioni sui simboli utilizzate per identificare e comprendere l'espressione analizzata.  
  
 Quando la valutazione dell'espressione asincrona è stata completata, viene inviato un evento asincrono per la Germania tramite Gestore di sessione di debug (SDM) per notificare l'IDE che la valutazione dell'espressione è stata completata. Una volta completata la valutazione dell'espressione sincrona, il risultato della valutazione viene restituito dalla chiamata al `IDebugExpression2::EvaluateSync` metodo.  
  
## <a name="implementation-notes"></a>Note di implementazione  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prevedono motori di debug comunicare con l'analizzatore di espressioni utilizzando le interfacce di Common Language Runtime (CLR). Di conseguenza, un analizzatore di espressioni che funziona con il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug devono supportare Common Language Runtime (un elenco completo di tutte le interfacce di debug di CLR è reperibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)