---
title: IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
- GetTypeFromPrimitive
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e58b4896b7935926904ecf37f4d8d130618d5961
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdynamicfieldcomplusgettypefromprimitive"></a>IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
Recupera un tipo dato il relativo tipo primitivo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetTypeFromPrimitive(  
   DWORD         dwCorElementType,  
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetTypeFromPrimitive(  
   uint            dwCorElementType,  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCorElementType`  
 [in] Valore di [enumerazione CorElementType](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) che rappresenta il tipo primitivo.  
  
 `ppType`  
 [out] Restituisce il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il tipo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)