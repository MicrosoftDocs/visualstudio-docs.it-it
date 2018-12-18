---
title: IDebugPort2::GetPortRequest | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6897c3085f14be785e4baaace0de7a4e92fea9ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Ottiene la descrizione di una porta utilizzata per creare la porta (se disponibile).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppRequest`  
 [out] Restituisce un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) oggetto che rappresenta la richiesta è stata utilizzata per creare la porta.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Restituisce `E_PORT_NO_REQUEST` se una porta non è stata creata utilizzando un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) richiesta porta.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)