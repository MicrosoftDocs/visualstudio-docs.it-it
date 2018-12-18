---
title: IDebugManagedObject | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7127d2583093ae06b52712cc6aacb0ea1adffc8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia consente l'analizzatore di espressioni (Java EE) per chiamare i metodi o proprietà su istanze di classi di valore (ad esempio, `System.Decimal`) e impostare il valore senza chiamare [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) nel programma sottoposto a debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto di codice gestito, ad esempio una variabile.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Per ottenere questa interfaccia, chiamare [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) su un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta un'istanza di una classe di valori.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati da [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugManagedObject` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Restituisce un'interfaccia che rappresenta l'oggetto di codice gestito e da quali appropriato del codice gestito è possibile ottenere l'interfaccia.|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Imposta il valore di questo oggetto per il valore di un oggetto di codice gestito specificato.|  
  
## <a name="remarks"></a>Note  
 Un analizzatore di espressioni utilizza questa interfaccia per archiviare un oggetto di codice gestito in un albero di analisi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [valutare](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)