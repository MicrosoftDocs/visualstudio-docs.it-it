---
title: IDebugArrayObject | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject
helpviewer_keywords: IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7a447a54fa0fcbc686cee0229c4c8dc6e80eeb20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta un oggetto matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni implementa questa interfaccia per rappresentare una matrice.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia può ottenere questa interfaccia con [QueryInterface](/cpp/atl/queryinterface) se l'oggetto rappresenta una matrice.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel `IDebugObject` interfaccia, i metodi seguenti vengono implementati nel `IDebugArrayObject` interfaccia.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Ottiene il numero di elementi nella matrice.|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Ottiene un elemento della matrice.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Ottiene tutti gli elementi della matrice.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Ottiene il numero di dimensioni della matrice.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Ottiene le dimensioni della matrice.|  
  
## <a name="remarks"></a>Note  
 Un analizzatore di espressioni utilizza questa interfaccia per rappresentare le matrici in una struttura ad albero di analisi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)