---
title: IDebugApplication::GetCurrentThread | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.GetCurrentThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::GetCurrentThread
ms.assetid: 15128e77-6fc6-42a2-8c04-20e22ef03f29
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2240a62b62c917e94f3ace8f516a10f9de66c74d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationgetcurrentthread"></a>IDebugApplication::GetCurrentThread
Restituisce il thread associato al thread attualmente in esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetCurrentThread(  
   IDebugApplicationThread**  pat  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pat`  
 [out] Il thread associato al thread attualmente in esecuzione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il thread associato al thread attualmente in esecuzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)