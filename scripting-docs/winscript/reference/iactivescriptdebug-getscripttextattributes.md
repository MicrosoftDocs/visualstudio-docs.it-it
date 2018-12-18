---
title: IActiveScriptDebug::GetScriptTextAttributes | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptDebug.GetScriptTextAttributes
apilocation: jscript.dll
helpviewer_keywords: IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8e9cd76da3e754eabce836b386893043dcd0622
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Restituisce gli attributi di testo per un blocco di testo dello script arbitrario.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrCode`  
 [in] Il testo di blocco di script. Questa stringa non deve essere con terminata null.  
  
 `uNumCodeChars`  
 [in] Il numero di caratteri nel testo del blocco di script.  
  
 `pstrDelimiter`  
 [in] Indirizzo del delimitatore di fine-di--blocco di script. Quando `pstrCode` viene analizzata da un flusso di testo, l'host in genere viene utilizzato un delimitatore, ad esempio due virgolette singole ("), per rilevare la fine del blocco di script. Questo parametro specifica il delimitatore che l'host utilizzato, consentendo il motore di script fornire alcuni condizionale primitivi pre-elaborazione (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) utilizzati dal motore scripting questa informazioni dipendono dal motore di script. Impostare questo parametro su NULL se l'host non ha utilizzato un delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwFlags`  
 [in] Flag associato al blocco di script. Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Indica che gli identificatori e operatori punto devono essere identificati con il flag SOURCETEXT_ATTR_IDENTIFIER e SOURCETEXT_ATTR_MEMBERLOOKUP, rispettivamente.|  
|GETATTRFLAG_THIS|0x0100|Indica che l'identificatore per l'oggetto corrente deve essere identificato con il flag SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Indica che testo della stringa di contenuto e commento deve essere identificato con il flag SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Buffer che deve contenere gli attributi restituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Uno smart host che implementa `IDebugDocumentText` interfaccia è possibile utilizzare questo metodo per delegare le chiamate al `IDebugDocumentText::GetText` metodo.  
  
 Questo metodo per blocchi di script. il `GetScriptletTextAttributes` è indicato per gli Scriptlet.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)