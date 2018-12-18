---
title: IActiveScriptSite::OnScriptTerminate | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eef8bd2a3f2e2a4eb4fd4b5f0e35fcd9acfe5bc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Comunica all'host che lo script ha completato l'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvarResult`  
 [in] Indirizzo di una variabile che contiene il risultato, script o `NULL` se lo script ha prodotto alcun risultato.  
  
 `pexcepinfo`  
 [in] Indirizzo di un `EXCEPINFO` struttura che contiene informazioni sull'eccezione generate quando lo script è terminata, o `NULL` se è stata generata alcuna eccezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`.  
  
## <a name="remarks"></a>Note  
 Il motore di script chiama questo metodo prima della chiamata al [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metodo, con il flag SCRIPTSTATE_INITIALIZED impostato, viene completata. Questo metodo può essere utilizzato per restituire lo stato di completamento e i risultati all'host. Si noti che molti linguaggi di script, basati sul sink di eventi dall'host, vita intervalli definiti dall'host. In questo caso, questo metodo non può mai chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)