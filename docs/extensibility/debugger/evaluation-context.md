---
title: Contesto di valutazione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 266fe85bedeea2c7e3dae7726d113d66a4b2b1e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="evaluation-context"></a>Contesto di valutazione
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando il motore di debug (DE) chiama l'analizzatore di espressioni (Java EE), tre argomenti passati a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinare il contesto per la ricerca e la valutazione di simboli, come illustrato nella tabella seguente.  
  
## <a name="arguments"></a>Argomenti  
  
|Argomento|Descrizione|  
|--------------|-----------------|  
|`pSymbolProvider`|Un [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaccia che specifica il gestore di simboli (SH) da utilizzare per identificare il simbolo.|  
|`pAddress`|Un [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaccia che specifica il punto di esecuzione corrente. Consente di individuare il metodo che contiene il codice in esecuzione.|  
|`pBinder`|Un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaccia che può essere utilizzato per trovare il valore e il tipo di un simbolo in base al nome.|  
  
 `IDebugParsedExpression::EvaluateSync` Restituisce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta il valore risultante e il relativo tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce dell'analizzatore di espressioni espressione chiave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [La visualizzazione delle variabili locali](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)