---
title: IDebugApplication::FCanJitDebug | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ca6b990011252bde581168a272da1041dc24f41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
Determina se un debugger di just-in-time (JIT) è registrato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo e un debugger JIT registrato, il metodo restituisce `TRUE`. In caso contrario restituirà `FALSE`.  
  
## <a name="remarks"></a>Note  
 Questo metodo determina se un debugger JIT è stato registrato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)