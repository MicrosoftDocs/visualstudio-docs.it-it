---
title: IDebugCustomAttribute::GetAttributeTypeField | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53511cf8549071795576c661e6a38f0c0973d269
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
Ottiene il tipo di classe di attributo personalizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAttributeTypeField(   
   IDebugClassField** ppCAType  
);  
```  
  
```csharp  
int GetAttributeTypeField(  
   out IDebugClassField ppCAType  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppCAType`  
 [out] Restituisce il [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto che rappresenta la classe di cui l'attributo personalizzato è un'istanza.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un attributo personalizzato è sempre una classe. Questo metodo fornisce l'accesso a un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto che descrive tale classe.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)