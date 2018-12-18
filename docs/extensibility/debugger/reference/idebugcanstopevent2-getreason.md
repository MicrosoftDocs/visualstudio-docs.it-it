---
title: IDebugCanStopEvent2::GetReason | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2::GetReason
helpviewer_keywords: IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 934ae1192a76cd7bd090c0cf2db384d28b61d6df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Ottiene il motivo per cui il motore di debug (DE) desidera arrestare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcr`  
 [out] Restituisce un valore di [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) enumerazione che descrive il motivo per questo evento.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene in genere chiamato prima di [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) metodo in modo che il chiamante può determinare se passare diverso da zero (`TRUE`) per il `IDebugCanStopEvent2::CanStop` metodo.  
  
 Il motivo per l'arresto può essere `CANSTOP_ENTRYPOINT`, ovvero la Germania ha raggiunto un punto di ingresso, o `CANSTOP_STEPIN`, ovvero la Germania ha eseguito l'accesso una funzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)