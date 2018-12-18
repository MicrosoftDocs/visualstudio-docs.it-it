---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a96a382c1dce73731fdd4326d8b0d1c35b7aa33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Restituisce un enumeratore di stack frame per il thread corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwSpMin`  
 [in] Limite inferiore dell'indirizzo per l'enumerazione di stack frame.  
  
 `ppedsf`  
 [out] Enumeratore degli stack frame per il thread corrente.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 L'enumeratore di frame dello stack restituisce i frame a partire dall'inizio dello stack, con il frame recentemente inserito. L'enumeratore contiene solo gli stack frame con indirizzi maggiori o uguale a `dwSpMin`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)