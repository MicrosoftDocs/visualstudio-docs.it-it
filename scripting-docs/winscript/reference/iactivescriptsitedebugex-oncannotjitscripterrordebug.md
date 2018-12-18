---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informa l'host su un errore in fase di esecuzione di script quando il processo di gestione esegue il Debug non viene trovato uno script debugger JIT.  
  
 Per implementare un debugger nell'host, è necessario gestire [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). In base a un'azione dell'utente, l'host può collegare il debugger e restituire o restituire l'avvio del debugger nel OnScriptErrorDebug `pfEnterDebugger` parametro. È inoltre necessario implementare questa interfaccia per ricevere le notifiche relative all'errore di runtime, anche se sono non presenti alcun debugger esterno che può essere interpretato dal gestore di eseguire il Debug del processo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pErrorDebug`  
 [in] Errore di run-time che si è verificato.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Se si desidera chiamare [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) se l'utente decide di continuare senza debug.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 È inoltre necessario implementare questa interfaccia per ottenere una notifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)