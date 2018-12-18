---
title: IDebugBinder::GetFunctionObject | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 302c6c983b07e2e2a7a393fac86999df4cb2b492
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Questo metodo ottiene un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) oggetto utilizzato per creare parametri di funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```csharp  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppFunction`  
 [out] Restituisce il [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia utilizzata per creare parametri di funzione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)