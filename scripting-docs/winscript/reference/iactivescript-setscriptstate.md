---
title: IActiveScript::SetScriptState | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 146cd5e4f2b6137fc6fe6e32e8ca153c3aab8fd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Inserisce lo stato specificato il motore di script. Questo metodo può essere chiamato dal thread non di base senza callout non in base a oggetti host o al [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ss`  
 [in] Imposta il motore di script per lo stato specificati. Può essere uno dei valori definiti nel [enumerazione SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_FAIL`|Il motore di script non supporta la transizione allo stato inizializzato. L'host deve ignorare il motore di script e creare, inizializzare e caricare un nuovo motore di scripting per ottenere lo stesso effetto.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script non è ancora caricato o inizializzato) e pertanto non è riuscita.|  
|`OLESCRIPT_S_PENDING`|Il metodo è stato accodato, ma lo stato non modificato ancora. Quando le modifiche di stato, il sito verrà chiamato nuovamente tramite il [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metodo.|  
|`S_FALSE`|Il metodo è riuscito, ma lo script è stato già nello stato specificato.|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sugli stati di motore di script, vedere la sezione di stati di motore di Script di [motori di Script Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)