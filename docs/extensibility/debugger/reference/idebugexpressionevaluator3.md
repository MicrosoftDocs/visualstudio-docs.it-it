---
title: IDebugExpressionEvaluator3 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator3 interface
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2349924dd2f762638dc6ea08b40a71776b9605a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluator3"></a>IDebugExpressionEvaluator3
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Rappresenta un analizzatore di espressioni (Java EE) con una struttura ad albero parser avanzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2  
```  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa versione del parser passa il provider di simboli e l'indirizzo della cornice di valutazione.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) interfaccia, implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|Converte una stringa di espressione in un'espressione analizzata specificata il provider di simboli e l'indirizzo della cornice di valutazione.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll