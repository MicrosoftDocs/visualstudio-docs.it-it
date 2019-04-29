---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63ce45c0973d65d240136d7b42aef0c078b00c9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992287"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Consente a un host specificare che deve terminare uno script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|La chiamata ha avuto esito positivo e l'host che consente lo script di continuare l'esecuzione.|  
|`S_FALSE`|La chiamata ha avuto esito positivo e le richieste di host che lo script termina.|  
  
## <a name="remarks"></a>Note  
 Lo script ospitato deve terminare a meno che il valore restituito del `QueryContinue` metodo `S_OK`. Valore restituito di `S_FALSE` indica che l'host in modo esplicito le richieste che lo script termina.  
  
 Un host a thread multipli può usare il `IActiveScript::InterruptScriptThread` metodo a terminare uno script.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)