---
title: IActiveScript::GetCurrentScriptThreadID | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Recupera un identificatore script-modulo di gestione-definito per il thread attualmente in esecuzione. L'identificatore può essere utilizzato nelle successive chiamate ai metodi di controllo dell'esecuzione di script thread, ad esempio il [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstidThread`  
 [out] Indirizzo di una variabile che riceve l'identificatore del thread script associato al thread corrente. L'interpretazione di questo identificatore viene lasciato al motore di script, ma può essere solo una copia dell'identificatore di thread di Windows. Se il thread Win32 termina, questo identificatore diventa non assegnato e successivamente può essere assegnato a un altro thread.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo, o `E_POINTER` se è stato specificato un puntatore non valido.  
  
## <a name="remarks"></a>Note  
 Questo metodo può essere chiamato dal thread non di base senza callout non in base a oggetti host o al [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)