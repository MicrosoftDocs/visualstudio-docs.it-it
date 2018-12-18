---
title: IDebugExpressionEvaluator | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5a4b7061b5de50162bd04e033a983987ab4f35f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta l'analizzatore di espressioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni deve implementare questa interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Per ottenere questa interfaccia, creare un'istanza dell'analizzatore di espressioni tramite il `CoCreateInstance` (metodo) con ID di classe (CLSID) dell'analizzatore. Vedere l'esempio.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugExpressionEvaluator`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Analisi](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Converte una stringa di espressione in un'espressione analizzata.|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Ottiene le variabili locali, argomenti e altre proprietà di un metodo.|  
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Converte un percorso di metodo e l'offset in un indirizzo di memoria.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Determina la lingua da utilizzare per creare risultati stampabili.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Imposta la radice del Registro di sistema. Usato per il debug side-by-side.|  
  
## <a name="remarks"></a>Note  
 In una situazione tipica, il motore di debug (DE) crea un'istanza dell'analizzatore di espressioni (Java EE) in seguito a una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Poiché la Germania conosce la lingua e il fornitore dell'amministratore che desidera utilizzare, la Germania Ottiene CLSID del motore di esecuzione dal Registro di sistema (il [SDK helper per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funzione `GetEEMetric`, risulta utile con l'operazione di recupero).  
  
 Dopo l'analizzatore di Espressioni viene creata un'istanza, la Germania chiama [analizzare](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per analizzare l'espressione e archiviarlo in un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto. In un secondo momento, una chiamata a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) valuta l'espressione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come creare un'istanza dell'analizzatore di espressioni specificato un provider di simboli e un indirizzo nel codice sorgente. In questo esempio viene utilizzata una funzione, `GetEEMetric`, dal [SDK helper per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) library, dbgmetric.lib.  
  
```cpp  
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,  
                                                 IDebugAddress *pSourceAddress)  
{  
    // This is typically defined globally but is specified here just  
    // for this example.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
  
    IDebugExpressionEvaluator *pEE = NULL;  
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {  
        HRESULT hr         = S_OK;  
        GUID  languageGuid = { 0 };  
        GUID  vendorGuid   = { 0 };  
  
        hr = pSymbolProvider->GetLanguage(pSourceAddress,  
                                          &languageGuid,  
                                          &vendorGuid);  
        if (SUCCEEDED(hr)) {  
            CLSID clsidEE      = { 0 };  
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;  
            // Get the expression evaluator's CLSID from the registry.  
            ::GetEEMetric(languageGuid,  
                          vendorGuid,  
                          metricCLSID,  
                          &clsidEE,  
                          strRegistrationRoot);  
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {  
                // Instantiate the expression evaluator.  
                spExpressionEvaluator.CoCreateInstance(clsidEE);  
            }  
            if (spExpressionEvaluator != NULL) {  
                pEE = spExpressionEvaluator.Detach();  
            }  
        }  
    }  
    return pEE;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)