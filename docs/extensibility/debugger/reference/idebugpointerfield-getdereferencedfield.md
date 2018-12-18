---
title: IDebugPointerField::GetDereferencedField | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77af1428dbdd0ea9f84000bda34ea8608b17cc24
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Questo metodo restituisce il tipo di oggetto a cui fa riferimento questo oggetto del puntatore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppField`  
 [out] Restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive il tipo di oggetto di destinazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se, ad esempio, il [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) oggetto punta a un numero intero, il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) tipo restituito da questo metodo viene descritto il tipo integer.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)