---
title: IDebugThreadCall::ThreadCallHandler | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugThreadCall.ThreadCallHandler
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugThreadCall::ThreadCallHandler
ms.assetid: c6d5d9db-bfed-44ec-90bc-46637f7de0ab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2b7a22026090c8b3b8b7ded4c960ebf92689cd4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugthreadcallthreadcallhandler"></a>IDebugThreadCall::ThreadCallHandler
Gestisce le chiamate per eseguire il codice in un altro thread.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ThreadCallHandler(  
   DWORD_PTR  dwParam1,  
   DWORD_PTR  dwParam2,  
   DWORD_PTR  dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwParam1`  
 [in] Il primo parametro.  
  
 `dwParam2`  
 [in] Il secondo parametro.  
  
 `dwParam3`  
 [in] Il terzo parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo gestisce le chiamate per eseguire il codice nel thread del debugger.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)   
 [IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)   
 [IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)