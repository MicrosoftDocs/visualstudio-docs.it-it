---
title: IEnumDebugObjects | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 99c6c7a98074753e9ee7e1364adb35e1cdba9700
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta una raccolta di oggetti che implementano il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni implementa questa interfaccia per fornire i set di oggetti che implementano il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia. Si noti che questo non è un'enumerazione standard COM a causa della presenza del [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) metodo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) restituisce questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Recupera il set successivo di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetti dall'enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Ignora un numero specificato di voci.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Reimposta l'enumerazione per la prima voce.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Recupera una copia dell'enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera il numero di voci dell'enumerazione.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia consente a un motore di debug per enumerare un set di oggetti in una matrice.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)