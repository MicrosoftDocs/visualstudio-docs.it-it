---
title: Architettura dell'analizzatore di espressioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fdcdfef67531af40027a2dfe8c731fe9ba5128f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator-architecture"></a>Architettura dell'analizzatore di espressioni
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'integrazione di un linguaggio proprietario nel pacchetto di debug di Visual Studio indica che l'implementazione delle interfacce obbligatorio espressione dell'analizzatore di espressioni (Java EE) e chiamare il provider in fase di esecuzione simbolo del linguaggio comune (SP) e interfacce dello strumento di associazione. Gli oggetti SP e strumento di associazione, oltre all'indirizzo corrente di esecuzione, sono il contesto in cui le espressioni vengono valutate. Le informazioni che queste interfacce producono e utilizzano rappresentano i concetti principali nell'architettura di un EE.  
  
## <a name="overview"></a>Panoramica  
  
### <a name="parsing-the-expression"></a>L'analisi dell'espressione  
 Quando si esegue il debug di un programma, le espressioni vengono valutate per svariati motivi, ma sempre quando il programma in fase di debug è stato arrestato in un punto di interruzione (l'utente inserita un punto di interruzione o uno causato da un'eccezione). È al momento quando Visual Studio Ottiene uno stack frame, come rappresentato dal [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia, dal motore di debug (DE). Visual Studio chiama quindi [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia. Questa interfaccia rappresenta un contesto in cui le espressioni possono essere valutate; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) è il punto di ingresso per il processo di valutazione. Fino a questo punto, tutte le interfacce vengono implementate per la Germania.  
  
 Quando `IDebugExpressionContext2::ParseText` viene chiamato, la Germania crea un'istanza di motore di esecuzione associato alla lingua del file di origine in cui si è verificato il punto di interruzione (la Germania un'istanza di SH a questo punto). L'analizzatore di Espressioni è rappresentato dal [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaccia. Chiama quindi la Germania [analizzare](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per convertire l'espressione, in formato testo, in un'espressione analizzata, pronto per la valutazione. Questa espressione analizzata è rappresentata dal [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaccia. Si noti che l'espressione viene in genere analizzato e non viene valutato a questo punto.  
  
 La Germania crea un oggetto che implementa il [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia, inserisce il `IDebugParsedExpression` nell'oggetto di `IDebugExpression2` oggetto e restituisce il `IDebugExpression2` dall'oggetto `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluating-the-expression"></a>La valutazione dell'espressione  
 Visual Studio chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per valutare l'espressione analizzata. Entrambi questi metodi chiamano [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` chiama il metodo immediatamente, mentre `IDebugExpression2::EvaluateAsync` chiama il metodo tramite un thread in background) per valutare l'espressione analizzata e restituire un [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il valore e il tipo dell'espressione analizzata. `IDebugParsedExpression::EvaluateSync` Usa fornito SH, indirizzo e dello strumento di associazione per convertire un valore effettivo, rappresentato dall'espressione analizzata la `IDebugProperty2` interfaccia.  
  
### <a name="for-example"></a>Per esempio  
 Dopo un punto di interruzione viene raggiunto un programma in esecuzione, l'utente sceglie di visualizzare una variabile nel **controllo immediato** la finestra di dialogo. Questa finestra di dialogo Mostra il nome della variabile, il relativo valore e il relativo tipo. L'utente può modificare in genere il valore.  
  
 Quando il **controllo immediato** viene visualizzata la finestra di dialogo, il nome della variabile di cui è in corso l'analisi viene inviato come testo [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Restituisce un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto che rappresenta l'espressione analizzata, in questo caso, la variabile. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) viene quindi chiamato per produrre un `IDebugProperty2` oggetto che rappresenta il valore della variabile e tipo, nonché il relativo nome. È questa informazioni visualizzate.  
  
 Se l'utente modifica il valore della variabile, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) viene chiamato con il nuovo valore, che modifica il valore della variabile in memoria in modo da utilizzare quando il programma riprende l'esecuzione.  
  
 Vedere [visualizzazione variabili locali](../../extensibility/debugger/displaying-locals.md) per ulteriori informazioni su questo processo di visualizzazione dei valori delle variabili. Vedere [la modifica del valore locale di](../../extensibility/debugger/changing-the-value-of-a-local.md) per ulteriori informazioni sul modo in cui viene modificato un valore della variabile.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Fornisce gli argomenti passati quando la Germania chiama l'analizzatore di Espressioni.  
  
 [Interfacce dell'analizzatore di espressioni chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Descrive le interfacce fondamentali necessarie quando si scrive un EE, insieme al contesto di valutazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [La visualizzazione delle variabili locali](../../extensibility/debugger/displaying-locals.md)   
 [Modifica del valore di una variabile locale](../../extensibility/debugger/changing-the-value-of-a-local.md)