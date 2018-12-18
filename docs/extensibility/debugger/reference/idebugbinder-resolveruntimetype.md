---
title: IDebugBinder::ResolveRuntimeType | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder::ResolveRuntimeType
helpviewer_keywords: IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fcaca4e27f7a4e986222e3fa6767a106ef6d90d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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