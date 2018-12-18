---
title: IDebugProcess3::GetDebugReason | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::GetDebugReason
helpviewer_keywords:
- IDebugProcess3::GetDebugReason
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b1db0cfea540458e0c8b288430027df03fa4cf2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess3getdebugreason"></a>IDebugProcess3::GetDebugReason
Questo metodo restituisce il motivo che il processo è stato avviato per il debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetDebugReason(  
   DEBUG_REASON* pReason  
);  
```  
  
```csharp  
int GetDebugReason(  
   out enum_DEBUG_REASON pReason  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pReason`  
 [out] Restituisce un valore di [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)