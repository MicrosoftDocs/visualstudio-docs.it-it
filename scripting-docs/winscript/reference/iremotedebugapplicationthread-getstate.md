---
title: IRemoteDebugApplicationThread::GetState | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce34fa73f97b92d08193c697e991c9e922ac17ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Ottiene lo stato di questo thread.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pState`  
 [out] Combinazione dei flag di stato di thread seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|Il thread è in esecuzione.|  
|THREAD_STATE_SUSPENDED|0x00000002|Il thread è sospeso.|  
|THREAD_BLOCKED|0x00000004|Il thread è bloccato.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|Il thread non rientra contenuto.|  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo ottiene lo stato di questo thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)