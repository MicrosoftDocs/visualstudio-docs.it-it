---
title: IDebugApplicationThread::QueryIsDebuggerThread | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsDebuggerThread
ms.assetid: 78a9cfbf-7c62-4aab-82a2-35037e2f9d46
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c3ad00fafa602b7a2f55b0412ae16c82cc2f5bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadqueryisdebuggerthread"></a>IDebugApplicationThread::QueryIsDebuggerThread
Determina se il thread è il thread del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT QueryIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito ed è il thread del debugger.|  
|`S_FALSE`|Non è il thread del debugger.|  
  
## <a name="remarks"></a>Note  
 Questo metodo determina se il thread è il thread del debugger.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)