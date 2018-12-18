---
title: IActiveScriptError::GetExceptionInfo | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetExceptionInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetExceptionInfo
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8719d1a169c89d7b6cf712a125b6962b9c7a8839
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
Recupera le informazioni sull'errore che si sono verificati durante l'esecuzione di uno script il motore di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pexcepinfo`  
 [out] Indirizzo di un `EXCEPINFO` struttura che riceve le informazioni di errore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo, o `E_FAIL` se si è verificato un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)