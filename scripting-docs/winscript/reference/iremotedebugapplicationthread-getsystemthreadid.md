---
title: 'IRemoteDebugApplicationThread:: GetSystemThreadId | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetSystemThreadId
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetSystemThreadId
ms.assetid: 6a6d5f62-4f60-4e87-9206-3c6f2e026d11
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35c281047bd3333f8fdc3945ed97ad3f402c53a4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575224"
---
# <a name="iremotedebugapplicationthreadgetsystemthreadid"></a>IRemoteDebugApplicationThread::GetSystemThreadId
Restituisce un identificatore dipendente dal sistema operativo associato al thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetSystemThreadId(  
   DWORD*  dwThreadId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwThreadId`  
 out Identificatore dipendente dal sistema operativo associato al thread.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Non è necessario che il valore di `dwThreadId` sia univoco tra i computer.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)