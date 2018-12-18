---
title: IRemoteDebugApplication::ConnectDebugger | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ConnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ConnectDebugger
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 538b7a3f76e6026297839e4a7a37e6c21a72d7d0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationconnectdebugger"></a>IRemoteDebugApplication::ConnectDebugger
Si connette un debugger all'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pad`  
 [in] Il debugger possa connettersi a questa applicazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Un debugger è già connesso a questa applicazione.|  
  
## <a name="remarks"></a>Note  
 Un'applicazione può avere solo un debugger collegato alla volta. Questo metodo non riesce se un debugger è già connesso.  
  
## <a name="see-also"></a>Vedere anche  
 [IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)   
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)