---
title: IDebugFunctionObject | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e7281be40e7559171c82da81d89f717bea3c8ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta una funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare una funzione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia è una specializzazione del [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) l'interfaccia e si ottiene utilizzando [QueryInterface](/cpp/atl/queryinterface) sul `IDebugObject` interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati da [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugFunctionObject` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Crea un oggetto di dati primitivi.|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Crea un oggetto utilizzando un costruttore.|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Crea un oggetto con alcun costruttore.|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Crea un oggetto matrice.|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Crea un oggetto stringa.|  
|[valutare](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Chiama la funzione e restituisce il valore risultante come oggetto.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia consente l'analizzatore di espressioni rappresentare funzioni in un albero di analisi. Il `Create` metodi in questa interfaccia vengono utilizzati per costruire oggetti che rappresentano i parametri di input al metodo. La funzione può quindi essere eseguita chiamando il [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) metodo, che restituisce un oggetto che rappresenta il valore restituito della funzione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)