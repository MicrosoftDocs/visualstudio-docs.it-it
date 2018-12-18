---
title: IDebugApplication::HandleRuntimeError | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eead4780ff061ff9c7280aeee0936c8f64741981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Causa il blocco del thread corrente e invia una notifica dell'errore per il debugger IDE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pErrorDebug`  
 [in] Errore verificatosi.  
  
 `pScriptSite`  
 [in] Il sito di script del thread.  
  
 `pbra`  
 [out] Azione da intraprendere quando il debugger consente di riprendere l'applicazione.  
  
 `perra`  
 [out] Azione da intraprendere quando il debugger consente di riprendere l'applicazione se si verifica un errore.  
  
 `pfCallOnScriptError`  
 [out] Flag che è `TRUE` se il motore deve chiamare il `IActiveScriptSite::OnScriptError` metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Un motore di linguaggio chiama questo metodo nel contesto di un thread che causa un errore di run-time. Questo metodo comporta il blocco del thread corrente e invia una notifica di errore da inviare al debugger IDE. Quando il debugger IDE riprende l'applicazione, questo metodo restituisce con l'azione da intraprendere.  
  
> [!NOTE]
>  Mentre nell'errore in fase di esecuzione, il motore di lingua può essere chiamato dal thread di eseguire tali attività come enumerare gli stack frame o valutare le espressioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfaccia IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Enumerazione ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)