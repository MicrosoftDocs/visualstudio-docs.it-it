---
title: IRemoteDebugApplicationEx:GetHostPid | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:GetHostPid
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:GetHostPid
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ffb5ff1d23c832f5710abf6d97199afe3f777b67
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationexgethostpid"></a>IRemoteDebugApplicationEx:GetHostPid
Restituisce l'ID di processo per l'applicazione host.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetHostPid(  
   DWORD*  dwHostPid  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwHostPid`  
 [out] L'identificatore di processo host.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Utilizzato dall'IDE.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplicationEx](http://msdn.microsoft.com/en-us/2f65fa67-06b7-4053-8945-22383ab66343)