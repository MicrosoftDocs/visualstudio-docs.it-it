---
title: IDebugFunctionObject2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6b051cc033f41f78fb1f2e6ed18eb22de6f8f0aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Rappresenta una funzione e migliora la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un analizzatore di espressioni (Java EE) implementa questa interfaccia per rappresentare una funzione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Metodi di questa interfaccia rinviare a quelli di **IDebugFunctionObject** nei modi seguenti:  
  
-   Il **IDebugEvaluate** accetta flag.  
  
-   Il **CreateObject** metodo accetta un timeout e flag.  
  
-   Il **CreateStringObjectWithLength** metodo accetta una lunghezza.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Crea un oggetto che usa un costruttore base impostazioni dei flag di valutazione e un valore di timeout.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Crea un oggetto stringa che ha la lunghezza specificata.|  
|[valutare](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Chiama la funzione e restituisce il valore risultante come oggetto.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll