---
title: IActiveScriptError::GetSourcePosition | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d63310a8ba5cfda39d48a482eaf7c345cd492adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Recupera la posizione nel codice sorgente in cui si è verificato un errore durante l'esecuzione di uno script il motore di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwSourceContext`  
 [out] Indirizzo di una variabile che riceve un cookie che identifica il contesto. L'interpretazione di questo parametro dipende dall'applicazione host.  
  
 `pulLineNumber`  
 [out] Indirizzo di una variabile che riceve il numero di riga nel file di origine in cui si è verificato l'errore.  
  
 `pichCharPosition`  
 [out] Indirizzo di una variabile che riceve la posizione del carattere nella riga in cui si è verificato l'errore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo, o `E_FAIL` se il percorso non è stato recuperato.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)