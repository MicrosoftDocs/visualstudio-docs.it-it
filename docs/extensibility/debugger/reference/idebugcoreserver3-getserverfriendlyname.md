---
title: IDebugCoreServer3::GetServerFriendlyName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 811292ff5f7dd95e127e63d30bf14ee06269ff7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Recupera un nome descrittivo per il server.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrName`  
 [out] Restituisce un nome descrittivo per il server.  
  
> [!NOTE]
>  Il chiamante è responsabile per liberare la stringa.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 Per i server utente ha avviato, il nome restituito da questo metodo è il nome completo del server. Per i server di avvio automatico, il nome è che del computer il server sia in esecuzione.  
  
 Per un nome macchina, chiamare il [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)