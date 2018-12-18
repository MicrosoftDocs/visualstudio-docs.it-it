---
title: IDebugCanStopEvent2::CanStop | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2::CanStop
helpviewer_keywords: IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7c5fe4c0ab03e6f0683fff3d43658fde5bc90bf0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica al motore di debug (DE) per arrestare in corrispondenza della posizione di codice o continua l'esecuzione o meno.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fCanStop`  
 [in] Diverso da zero (`TRUE`) se la Germania deve essere interrotta in corrispondenza della posizione di codice; in caso contrario, zero (`FALSE`).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il destinatario di questo evento chiama in genere il [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodo per determinare il motivo per la Germania desidera arrestare, quindi chiama il `IDebugCanStopEvent2::CanStop` metodo con la risposta appropriata.  
  
 Se si arresta la Germania, invia un evento che descrive il motivo dell'arresto. Sono disponibili due eventi che vengono inviati, rappresentata da un'interruzione di utente o dei segnali di [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interfaccia e un evento punto di interruzione rappresentato dal [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)