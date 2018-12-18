---
title: IDebugStackFrameSniffer::EnumStackFrames | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugStackFrameSniffer.EnumStackFrames
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSniffer::EnumStackFrames
ms.assetid: a7629ab3-ef7d-4bbe-a137-bb2a8ad0f384
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d64d896dcc14a280a74f64f5093b6708a7fcb5f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferenumstackframes"></a>IDebugStackFrameSniffer::EnumStackFrames
Restituisce un enumeratore di stack frame per il thread corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppedsf`  
 [out] Enumeratore degli stack frame per il thread corrente.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 L'enumeratore di frame dello stack restituisce i frame a partire dall'inizio dello stack, a partire dal frame recentemente inserito.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)