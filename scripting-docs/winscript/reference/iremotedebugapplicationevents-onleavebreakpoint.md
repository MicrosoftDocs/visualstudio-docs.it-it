---
title: IRemoteDebugApplicationEvents::OnLeaveBreakPoint | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnLeaveBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnLeaveBreakPoint
ms.assetid: 00449a23-1f67-4078-ad06-4c426abf7587
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9afb48ceca742ef736dd8f79ba8c3d96e3a56a82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationeventsonleavebreakpoint"></a>IRemoteDebugApplicationEvents::OnLeaveBreakPoint
Gestisce un evento per cui un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnLeaveBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `prdat`  
 [in] Il thread dell'applicazione che a sinistra del punto di interruzione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo gestisce un evento per cui un punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)