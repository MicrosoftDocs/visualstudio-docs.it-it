---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation: jscript.dll
helpviewer_keywords: IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40fd8e2d19d3949ff26811956ae3d203871e5510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Utilizzata da un host intelligente per delegare il `IDebugDocumentContext::EnumCodeContexts` metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwSourceContext`  
 [in] Il contesto di origine come fornita a `IActiveScriptParse::ParseScriptText` o `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Carattere spostato rispetto all'inizio del testo dello script.  
  
 `uNumChars`  
 [in] Numero di caratteri in questo contesto.  
  
 `ppescc`  
 [out] Un enumeratore dei contesti di codice nell'intervallo specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 SmartHost utilizzare questo metodo per delegare il `IDebugDocumentContext::EnumCodeContexts` metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)