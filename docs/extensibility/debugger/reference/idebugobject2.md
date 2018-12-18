---
title: IDebugObject2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2
helpviewer_keywords: IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 40b52cf5c36db3bf4fa07004df9a171e77c2520e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia fornisce informazioni aggiuntive su un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni implementa questa interfaccia per offre il supporto per gli alias e l'accesso alle informazioni sull'oggetto.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia può ottenere questa interfaccia con [QueryInterface](/cpp/atl/queryinterface). Inoltre, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) restituisce questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia, il `IDebugObject2` interfaccia implementa le operazioni seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Ottiene il campo o una variabile (se presente) che può essere supporto della proprietà rappresentata dall'oggetto.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Ottiene l'oggetto di codice gestito che rappresenta il valore di questo oggetto.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Crea un ID univoco per questo oggetto o restituisce un alias esistente.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Ottiene l'alias associato all'oggetto, se presente.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Ottiene il tipo di questo oggetto.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Determina se questo oggetto rappresenta i dati utente.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Determina se lo stato di modifica e continuazione non è più valido.<br /><br /> Un analizzatore di espressioni personalizzato non implementa questo metodo (deve sempre restituire `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Note  
 Vedere [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) per una discussione sugli alias.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)