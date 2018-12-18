---
title: La valutazione di un'espressione di controllo finestra | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: beb632b484659c3bc901142b35ab52d25b8067fe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="evaluating-a-watch-window-expression"></a>La valutazione di un'espressione di finestra di controllo
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando viene sospesa l'esecuzione, Visual Studio chiama il motore di debug (DE) per determinare il valore corrente di ogni espressione nell'elenco di espressioni di controllo. La Germania valuta ogni espressione utilizzando un analizzatore di espressioni (Java EE) e Visual Studio consente di visualizzare il valore di **espressioni di controllo** finestra.  
  
 Di seguito è riportata una panoramica delle modalità di valutazione di un'espressione di controllo elenco:  
  
1.  Visual Studio chiama il DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il contesto di un'espressione che può essere usato per valutare le espressioni.  
  
2.  Per ogni espressione nell'elenco di controllo, Visual Studio chiama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per convertire il testo dell'espressione in un'espressione analizzata.  
  
3.  `IDebugExpressionContext2::ParseText` le chiamate [analizzare](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per eseguire il lavoro effettivo dell'analisi di testo e producono un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto.  
  
4.  `IDebugExpressionContext2::ParseText` Crea un' [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto e inserisce il `IDebugParsedExpression` oggetti al suo interno. Questo si`DebugExpression2` viene quindi restituito a Visual Studio.  
  
5.  Chiamate di Visual Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per valutare l'espressione analizzata.  
  
6.  `IDebugExpression2::EvaluateSync` passa la chiamata a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) per eseguire la valutazione effettiva e produrre un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto restituito a Visual Studio.  
  
7.  Chiamate di Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ottenere il valore dell'espressione che viene quindi visualizzato nell'elenco di controllo.  
  
## <a name="parse-then-evaluate"></a>Analizzare quindi valutare  
 Poiché l'analisi di un'espressione complessa può richiedere molto più lunga della valutazione, il processo di valutazione di un'espressione è suddiviso in due passaggi: 1) consente di analizzare l'espressione e 2) consente di valutare l'espressione analizzata. In questo modo, una valutazione può verificarsi più volte, ma l'espressione deve essere analizzata una sola volta. L'espressione analizzata intermedia viene restituito dal motore di esecuzione in un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto che a sua volta è incapsulato e restituito dalla Germania come un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto. Il `IDebugExpression` oggetto Rinvia tutti della valutazione di `IDebugParsedExpression` oggetto.  
  
> [!NOTE]
>  Non è necessario per un EE rispettare questo processo in due passaggi anche se Visual Studio si presuppone che questo oggetto. l'analizzatore di Espressioni può analizzare e valutare nello stesso passaggio quando [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) viene chiamato (questo è l'esempio MyCEE funzionamento, ad esempio). Se la lingua può creare espressioni complesse, si desidera separare il passaggio di analisi del passaggio di valutazione. Ciò può migliorare le prestazioni nel debugger di Visual Studio quando molte espressioni di controllo vengono visualizzate.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione di esempio di valutazione delle espressioni](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Utilizza l'esempio MyCEE per scorrere il processo di valutazione dell'espressione.  
  
 [Valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Viene illustrato che cosa avviene dopo un'analisi dell'espressione ha esito positivo.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Fornisce gli argomenti passati quando il motore di debug (DE) chiama l'analizzatore di espressioni (Java EE).  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)