---
title: IActiveScript::SetScriptSite | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11fa9003abb03c42adcbf3a548bb5b90d763a344
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Segnala al motore di scripting di [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) sito interfaccia fornita dall'host. Chiamare questo metodo prima di qualsiasi altro [IActiveScript](../../winscript/reference/iactivescript.md) metodi di interfaccia viene utilizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pScriptSite`  
 [in] Indirizzo del sito da associare a questa istanza del motore di scripting fornita dall'host di script. Il sito deve essere assegnato in modo univoco a questa istanza del motore di scripting; non può essere condiviso con altri motori di script.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_FAIL`|Si è verificato un errore non specificato; il motore di script non è stata completata l'inizializzazione del sito.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, un sito è stato già impostato).|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)