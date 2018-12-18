---
title: IDebugBinder | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3514d280b6718fc670f3bdac35b6bbacbbf2b09c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia associa un campo di simboli, in genere restituito dal provider di simboli, per un contesto di memoria o un oggetto che contiene il valore corrente del simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia supporta la valutazione dell'espressione e deve essere implementata dal motore di debug (DE).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene utilizzata nel processo di valutazione dell'espressione e viene in genere utilizzata nell'implementazione di [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugBinder`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Operazione di binding](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ottiene il contesto di memoria o di un oggetto che contiene il valore corrente del simbolo.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina il tipo in fase di esecuzione di un oggetto.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Converte un indirizzo di memoria o percorso oggetto in un contesto di memoria.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ottiene un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) oggetto utilizzato per creare parametri di funzione.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ottiene il tipo esatto per una variabile.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia restituisce gli oggetti utilizzati dall'analizzatore di espressioni in strutture di analisi. L'analizzatore di espressioni analizza un'espressione tramite il provider di simboli per convertire i simboli dell'espressione in istanze di [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), che descrivono ogni simbolo posizione nel codice sorgente e di tipo. Il [associare](../../../extensibility/debugger/reference/idebugbinder-bind.md) metodo converte `IDebugField` oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) gli oggetti che la connessione o il binding di un simbolo di tipo a un valore effettivo in memoria. Questi `IDebugObject` gli oggetti vengono quindi archiviati in una struttura ad albero di analisi per la valutazione successiva.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)