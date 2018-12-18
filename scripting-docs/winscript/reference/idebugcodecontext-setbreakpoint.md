---
title: IDebugCodeContext::SetBreakPoint | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugCodeContext.SetBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::SetBreakPoint
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a0111deba23f29aa6b7d31a1aed8d729ff4e7fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
Imposta o cancella un punto di interruzione in questo contesto di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bps`  
 [in] Specifica lo stato del punto di interruzione per il contesto del codice.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo imposta o cancella un punto di interruzione in questo contesto di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)   
 [Enumerazione BREAKPOINT_STATE](../../winscript/reference/breakpoint-state-enumeration.md)