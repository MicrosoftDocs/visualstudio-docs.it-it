---
title: Implementazione della valutazione dell'espressione di esempio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9edc31a8bc403f4f6dfcb16847d3cfce5d99b526
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sample-implementation-of-expression-evaluation"></a>Implementazione di esempio della valutazione dell'espressione
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Per un **espressioni di controllo** espressione finestra, le chiamate di Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per produrre un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto. `IDebugExpressionContext2::ParseText` Crea un'istanza di un analizzatore di espressioni (Java EE) e chiama [analizzare](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per ottenere un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto.  
  
 Questa implementazione di `IDebugExpressionEvaluator::Parse` esegue le attività seguenti:  
  
1.  [Solo C++] Analizza l'espressione per cercare errori.  
  
2.  Crea un'istanza di una classe (chiamato `CParsedExpression` in questo esempio) che implementa il `IDebugParsedExpression` interfaccia e archivia nella classe l'espressione deve essere analizzato.  
  
3.  Restituisce il `IDebugParsedExpression` interfaccia dal `CParsedExpression` oggetto.  
  
> [!NOTE]
>  Negli esempi che seguono e nell'esempio MyCEE, l'analizzatore di espressioni non separare l'analisi della valutazione.  
  
## <a name="managed-code"></a>Codice gestito  
 Si tratta di un'implementazione di `IDebugExpressionEvaluator::Parse` nel codice gestito. Si noti che questa versione del metodo rinvia l'analisi per [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) come il codice per l'analisi anche valuta contemporaneamente (vedere [la valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT Parse(  
                string                 expression,   
                uint                   parseFlags,  
                uint                   radix,  
            out string                 errorMessage,   
            out uint                   errorPosition,   
            out IDebugParsedExpression parsedExpression)  
        {   
            errorMessage = "";  
            errorPosition = 0;  
  
            parsedExpression =  
                new CParsedExpression(parseFlags, radix, expression);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Codice non gestito  
 Si tratta di un'implementazione di `IDebugExpressionEvaluator::Parse` nel codice non gestito. Questo metodo chiama una funzione di supporto, `Parse`, analizzare l'espressione e il controllo degli errori, ma questo metodo ignora il valore risultante. La valutazione formale è posticipata per [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) in cui l'espressione viene analizzato quando viene valutata (vedere [la valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```cpp  
STDMETHODIMP CExpressionEvaluator::Parse(  
        in    LPCOLESTR                 pszExpression,  
        in    PARSEFLAGS                flags,  
        in    UINT                      radix,  
        out   BSTR                     *pbstrErrorMessages,  
        inout UINT                     *perrorCount,  
        out   IDebugParsedExpression  **ppparsedExpression  
    )  
{  
    if (pbstrErrorMessages == NULL)  
        return E_INVALIDARG;  
    else  
        *pbstrErrormessages = 0;  
  
    if (pparsedExpression == NULL)  
        return E_INVALIDARG;  
    else  
        *pparsedExpression = 0;  
  
    if (perrorCount == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    // Look for errors in the expression but ignore results  
    hr = ::Parse( pszExpression, pbstrErrorMessages );  
    if (hr != S_OK)  
        return hr;  
  
    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );  
    if (!pparsedExpr)  
        return E_OUTOFMEMORY;  
  
    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,  
                                      reinterpret_cast<void**>(ppparsedExpression) );  
    pparsedExpr->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [La valutazione di un'espressione di finestra di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)