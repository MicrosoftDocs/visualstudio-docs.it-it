---
title: IDebugApplicationThread::SynchronousCallIntoThread | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdeb57380975f19424f8b7da783846b5aae976ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Fornisce un meccanismo per il chiamante può eseguire codice nel thread dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstcb`  
 [in] Oggetto da chiamare.  
  
 `dwParam1`  
 [in] Primo parametro da passare per il `IDebugThreadCall::ThreadCallHandler` metodo.  
  
 `dwParam2`  
 [in] Secondo parametro da passare per il `IDebugThreadCall::ThreadCallHandler` metodo.  
  
 `dwParam3`  
 [in] Terzo parametro da passare per il `IDebugThreadCall::ThreadCallHandler` metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo fornisce un meccanismo per il chiamante eseguire il codice nel thread del debugger. Gli host e motori di linguaggio utilizzano in genere questo metodo per implementare gli oggetti a thread libero sopra le implementazioni a thread singole.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)   
 [Interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)