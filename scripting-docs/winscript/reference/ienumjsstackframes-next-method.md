---
title: 'Metodo ienumjsstackframes:: Next | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumJsStackFrames.Next
apilocation: jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2068bd130e7eb03747b89e2ba107019aa1cd458
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ienumjsstackframesnext-method"></a>Metodo IEnumJsStackFrames::Next
Ottiene il numero di frame specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cFrameCount`  
 [in] Il numero di frame da ottenere.  
  
 `pFrames`  
 [out] Matrice in cui archiviare i frame.  
  
 `pcFetched`  
 [out] Ha restituito il numero di fotogrammi.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumJsStackFrames](../../winscript/reference/ienumjsstackframes-interface.md)