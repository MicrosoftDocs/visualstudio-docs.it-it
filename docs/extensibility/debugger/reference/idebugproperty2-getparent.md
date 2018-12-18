---
title: IDebugProperty2::GetParent | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad6e4688a840f9fb90a46f94d4a2d48eb1be702a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
Ottiene la proprietà padre di una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetParent (   
   IDebugProperty2** ppParent  
);  
```  
  
```csharp  
int GetParent (   
   out IDebugProperty2 ppParent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppParent`  
 [out] Restituisce un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta l'elemento padre della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore. Restituisce `S_GETPARENT_NO_PARENT` se è presente alcun padre.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)