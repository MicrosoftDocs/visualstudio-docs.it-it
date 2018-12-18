---
title: IActiveScriptError::GetSourceLineText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptError.GetSourceLineText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptError_GetSourceLineText
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb886d5f40042313483dc3b298488d1291c30563
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
Recupera la riga nel file di origine in cui si è verificato un errore durante l'esecuzione di uno script di un motore di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>Parametro  
 `pbstrSourceLine`  
 [out] Indirizzo di un buffer che riceve la riga del codice sorgente in cui si è verificato l'errore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo, o `E_FAIL` se non è stata recuperata la riga nel file di origine.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)