---
title: IDebugParsedExpression | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b877dd974a0b96a176b54f308a6317e7324b6ab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta un'espressione analizzata pronta per essere valutata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un'espressione analizzata che è pronta per la valutazione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [analizzare](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) restituisce questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente mostra il metodo di `IDebugParsedExpression`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Valuta l'espressione analizzata.|  
  
## <a name="remarks"></a>Note  
 Quando il chiamante è pronto per la valutazione dell'espressione, chiama [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) per restituire un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che contiene il risultato della valutazione. Questo approccio a due parti per la valutazione, l'analisi, la valutazione, consente all'espressione analizzata deve essere valutata più volte, ignorando il lungo processo di analisi dell'espressione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)