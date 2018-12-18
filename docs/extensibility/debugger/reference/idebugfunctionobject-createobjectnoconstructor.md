---
title: IDebugFunctionObject::CreateObjectNoConstructor | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d641fa8dc0f999d55d177e9a3f48e0227e17f159
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Crea un oggetto con alcun costruttore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pClassObject`  
 [in] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta il tipo dell'oggetto da creare.  
  
 `ppObject`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'oggetto appena creato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Chiamare questo metodo per creare un oggetto che rappresenta un'istanza di una struttura o un tipo complesso (che non richiedono un costruttore) che è un parametro della funzione rappresentata dal [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.  
  
 Se il parametro dell'oggetto richiede un costruttore, chiamare il [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)