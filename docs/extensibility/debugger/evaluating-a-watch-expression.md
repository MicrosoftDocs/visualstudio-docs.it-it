---
title: La valutazione di un'espressione di controllo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d86b94a457934547037f2428e6284f20de1660d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="evaluating-a-watch-expression"></a>La valutazione di un'espressione di controllo
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando Visual Studio è pronto per visualizzare il valore di un'espressione di controllo, chiama [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) che a sua volta chiama [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Ciò produce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che contiene il valore e il tipo dell'espressione.  
  
 In questa implementazione di `IDebugParsedExpression::EvaluateSync`, l'espressione viene analizzata e valutata nello stesso momento. Questa implementazione esegue le attività seguenti:  
  
1.  Analizza e valuta l'espressione per produrre un oggetto generico che contiene il valore e il relativo tipo. In c#, questa viene rappresentata come un `object` mentre in C++ rappresentati come un `VARIANT`.  
  
2.  Crea un'istanza di una classe (chiamato `CValueProperty` in questo esempio) che implementa il `IDebugProperty2` interfaccia e archivia nella classe il valore da restituire.  
  
3.  Restituisce il `IDebugProperty2` interfaccia dal `CValueProperty` oggetto.  
  
## <a name="managed-code"></a>Codice gestito  
 Si tratta di un'implementazione del `IDebugParsedExpression::EvaluateSync` nel codice gestito. Il metodo helper `Tokenize` analizza l'espressione in un albero di analisi. La funzione di supporto `EvalToken` converte il token in un valore. La funzione di supporto `FindTerm` in modo ricorsivo attraversa la struttura di analisi, la chiamata `EvalToken` per ogni nodo che rappresenta un valore e l'applicazione di qualsiasi operazione (addizione o sottrazione) nell'espressione.  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT EvaluateSync(  
            uint evalFlags,  
            uint timeout,  
            IDebugSymbolProvider provider,  
            IDebugAddress address,  
            IDebugBinder binder,  
            string resultType,  
            out IDebugProperty2 result)  
        {  
            HRESULT retval = COM.S_OK;  
            this.evalFlags = evalFlags;  
            this.timeout = timeout;  
            this.provider = provider;  
            this.address = address;  
            this.binder = binder;  
            this.resultType = resultType;  
  
            try  
            {  
                IDebugField field = null;  
                // Tokenize, then parse.  
                tokens = Tokenize(expression);  
                result = new CValueProperty(  
                             expression,  
                             (int) FindTerm(EvalToken(tokens[0], out field),1),  
                             field,  
                             binder);  
            }  
            catch (ParseException)  
            {  
                result = new CValueProperty(expression, "Huh?");  
                retval = COM.E_INVALIDARG;  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Codice non gestito  
 Si tratta di un'implementazione del `IDebugParsedExpression::EvaluateSync` nel codice non gestito. La funzione di supporto `Evaluate` analizza e valuta l'espressione, restituendo un `VARIANT` contenente il valore risulta. La funzione di supporto `VariantValueToProperty` bundle di `VARIANT` in un `CValueProperty` oggetto.  
  
```  
[C++]  
STDMETHODIMP CParsedExpression::EvaluateSync(   
    in  DWORD                 evalFlags,  
    in  DWORD                 dwTimeout,  
    in  IDebugSymbolProvider* pprovider,  
    in  IDebugAddress*        paddress,  
    in  IDebugBinder*         pbinder,  
    in  BSTR                  bstrResultType,  
    out IDebugProperty2**     ppproperty )  
{  
    // dwTimeout parameter is ignored in this implementation.  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (paddress == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    VARIANT value;  
    BSTR    bstrErrorMessage = NULL;  
    hr = ::Evaluate( pprovider,  
                     paddress,  
                     pbinder,  
                     m_expr,  
                     &bstrErrorMessage,  
                     &value );  
    if (hr != S_OK)  
    {  
        if (bstrErrorMessage == NULL)  
            return hr;  
  
        //we can display better messages ourselves.  
        HRESULT hrLocal = S_OK;  
        VARIANT varType;  
        VARIANT varErrorMessage;  
  
        VariantInit( &varType );  
        VariantInit( &varErrorMessage );  
        varErrorMessage.vt      = VT_BSTR;  
        varErrorMessage.bstrVal = bstrErrorMessage;  
  
        CValueProperty* valueProperty = new CValueProperty();  
        if (valueProperty != NULL)  
        {  
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);  
            if (SUCCEEDED(hrLocal))   
            {  
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,  
                        reinterpret_cast<void**>(ppproperty) );  
            }  
        }  
  
        VariantClear(&varType);  
        VariantClear(&varErrorMessage); //frees BSTR  
        if (!valueProperty)  
            return hr;  
        valueProperty->Release();  
        if (FAILED(hrLocal))  
            return hr;  
    }  
    else  
    {  
        if (bstrErrorMessage != NULL)  
            SysFreeString(bstrErrorMessage);  
  
        hr = VariantValueToProperty( pprovider,  
                                     paddress,  
                                     pbinder,  
                                     m_radix,  
                                     m_expr,  
                                     value,  
                                     ppproperty );  
        VariantClear(&value);  
        if (FAILED(hr))  
            return hr;  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [La valutazione di un'espressione di finestra di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Implementazione di esempio di valutazione delle espressioni](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)