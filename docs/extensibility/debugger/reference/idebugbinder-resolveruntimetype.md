---
title: IDebugBinder::ResolveRuntimeType | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6aa911dba9d56996e048326737c1dd99ca89c49c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Questo metodo determina il tipo in fase di esecuzione di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```csharp  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pObject`  
 [in] Il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) da risolvere.  
  
 `ppResolved`  
 [out] Restituisce il tipo dell'oggetto come un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il tipo in fase di esecuzione di un oggetto non è sempre noto in fase di compilazione. Ad esempio, il polimorfismo, un argomento può essere passato a una funzione come classe base, ad esempio una classe del pulsante. L'argomento effettivo potrebbe essere una classe derivata, ad esempio una classe di pulsante di opzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)