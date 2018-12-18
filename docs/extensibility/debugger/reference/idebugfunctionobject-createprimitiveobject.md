---
title: IDebugFunctionObject::CreatePrimitiveObject | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 477bdb12cef6711c6b946b3ddd8d9550e48c01b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Crea un oggetto di dati primitivi, ad esempio un numero intero semplice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ot`  
 [in] Un valore di [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) enumerazione che rappresenta il tipo di primitiva da creare.  
  
 `ppObject`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'oggetto appena creato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Chiamare questo metodo per creare un oggetto che rappresenta un oggetto di base che è un parametro alla funzione che è rappresentato dal [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia. Ad esempio, se la stringa dell'espressione è "myString(5)", questo metodo viene utilizzato per creare un oggetto che rappresenta l'intero 5.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)