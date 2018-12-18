---
title: IActiveScript::Close | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Fa sì che il motore di script per l'abbandono di tutti gli script caricati, perdono il proprio stato e rilasciare qualsiasi puntatori a interfaccia che dispone di altri oggetti, quindi immettere uno stato chiuso. Sink di evento, il testo script eseguito immediatamente e le chiamate alle macro che sono già in corso vengono completati prima i cambiamenti di stato (utilizzare [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) per annullare un thread in esecuzione di script). Questo metodo deve essere chiamato dall'host di creazione prima che l'interfaccia viene rilasciata per evitare problemi relativi ai riferimenti circolari.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script era già in stato di chiusura).|  
|`OLESCRIPT_S_PENDING`|Il metodo è stato accodato, ma lo stato non modificato ancora. Quando le modifiche di stato, il sito è richiamata sul [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metodo.|  
|`S_FALSE`|Il metodo è riuscito, ma lo script è già stato chiuso.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)