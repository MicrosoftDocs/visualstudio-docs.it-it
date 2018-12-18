---
title: IDebugApplication::FIsAutoJitDebugEnabled | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.FIsAutoJitDebugEnabled
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 268a10cc829e2d217bb9a90b355405dd8f3b15b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Determina se un debugger di just-in-time (JIT) è registrato in host dumb auto-debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo e un debugger JIT è registrato in host dumb auto-debug, il metodo restituisce `TRUE`. In caso contrario restituirà `FALSE`.  
  
## <a name="remarks"></a>Note  
 Questo metodo determina se un debugger JIT è registrato con host dumb auto-debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)