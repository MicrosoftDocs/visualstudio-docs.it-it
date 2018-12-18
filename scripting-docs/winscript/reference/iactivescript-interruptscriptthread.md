---
title: IActiveScript::InterruptScriptThread | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.InterruptScriptThread
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad717ee950dda4f0f0d7a14292f0f5f150ab4973
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Interrompe l'esecuzione di un thread in esecuzione di script (un sink di evento, un'esecuzione immediata o una chiamata di macro). Questo metodo può essere utilizzato per terminare uno script che è bloccato (ad esempio, in un ciclo infinito). Può essere chiamato dal thread non di base senza callout non in base a oggetti host o al [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stidThread`  
 [in] Identificatore del thread interrupt, o su uno dei valori di identificatore thread speciali seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Tutti i thread. L'interrupt viene applicata a tutti i metodi di script in corso. Si noti che, a meno che il chiamante ha richiesto che lo script di disconnessione, l'evento successivo tramite script comporta il codice di script eseguire di nuovo chiamando il [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) metodo con il SCRIPTSTATE_DISCONNECTED o SCRIPTSTATE_INITIALIZED flag impostato.|  
|SCRIPTTHREADID_BASE|Il thread di base. vale a dire il thread in cui la creazione di script del motore è stata creata un'istanza.|  
|SCRIPTTHREADID_CURRENT|Il thread attualmente in esecuzione.|  
  
 `pexcepinfo`  
 [in] Indirizzo di un `EXCEPINFO` struttura che contiene le informazioni sull'errore che devono essere segnalati allo script interrotte.  
  
 `dwFlags`  
 [in] Flag di opzione associati l'interruzione. Può essere uno dei seguenti valori:  
  
|Valore|Significato|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Se supportato, immettere il debugger del motore di script in fase di esecuzione dello script corrente.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Se supportato dal linguaggio di scripting del motore, lasciare lo script gestisce l'eccezione. In caso contrario, il metodo di script viene interrotta e viene restituito il codice di errore per il chiamante. vale a dire l'invoker di evento origine o una macro.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script non è ancora caricato o inizializzato).|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)