---
title: 'Metodo ijsdebugbreakpoint:: IsEnabled | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJSDebugBreakPoint.IsEnabled
apilocation: jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb7ab887b8e3442a0c38ea403ad43bdea10cdd66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugbreakpointisenabled-method"></a>Metodo IJsDebugBreakPoint::IsEnabled
Determina se il punto di interruzione è abilitato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pIsEnabled`  
 [out] Restituisce true se il punto di interruzione è abilitato. in caso contrario, restituisce false.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce E_UNEXPECTED se chiamato su un punto di interruzione eliminato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)