---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteInterruptPoll.QueryContinue
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Consente a un host specificare che deve terminare uno script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|La chiamata ha avuto esito positivo e l'host che consente lo script di continuare l'esecuzione.|  
|`S_FALSE`|La chiamata ha avuto esito positivo e le richieste di host che lo script termina.|  
  
## <a name="remarks"></a>Note  
 Lo script ospitato deve terminare, a meno che il valore restituito del `QueryContinue` metodo `S_OK`. Valore restituito di `S_FALSE` indica che l'host in modo esplicito le richieste che lo script termina.  
  
 Un host con multithreading è possibile utilizzare il `IActiveScript::InterruptScriptThread` metodo per interrompere uno script.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)