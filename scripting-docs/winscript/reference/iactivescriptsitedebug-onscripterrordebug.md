---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a669d435d84295b22af4298936babf8439eaefa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Consente a un host intelligente stabilire come gestire errori di run-time.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pErrorDebug`  
 [in] Errore di run-time che si sono verificati  
  
 `pfEnterDebugger`  
 [out] Flag che indica se l'errore di passare al debugger di eseguire il debug JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Flag che indica se chiamare `IActiveScriptSite::OnScriptError` quando l'utente decide di continuare senza debug.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati al valore nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Uno smart host può utilizzare questo metodo per determinare come gestire errori di run-time.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)