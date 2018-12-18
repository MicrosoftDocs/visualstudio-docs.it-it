---
title: IDebugArrayObject::GetElements | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae1d22af6796c2de72c763137c8f96feb7885407
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Ottiene un enumeratore di tutti gli elementi della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) oggetto che consente l'enumerazione su tutti gli elementi.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In alternativa, utilizzare il [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) e [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metodi per scorrere gli elementi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)