---
title: IDebugApplication::SynchronousCallInDebuggerThread | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.SynchronousCallInDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7b66b0b085c0fe3abbee3c3b8c5c3f7d252d3b5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Fornisce un meccanismo per il chiamante eseguire il codice nel thread del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pptc`  
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
 Gli host e motori di linguaggio utilizzano in genere questo metodo per implementare gli oggetti a thread libero sopra le implementazioni a thread singole.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)