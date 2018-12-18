---
title: IDebugDocumentHost::GetScriptTextAttributes | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 517b228bb46594d19ba6d2fdf41a68e22ac03c75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Restituisce gli attributi di testo per un blocco di testo del documento.  
  
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
 [in] Il testo di blocco di script. Non è necessario che questa stringa di terminazione null.  
  
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
|`E_NOTIMPL`|L'host Usa solo gli attributi predefiniti.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce gli attributi di testo per un blocco arbitrario del testo del documento. È accettabile per gli host restituire `E_NOTIMPL`, nel qual caso vengono utilizzati gli attributi predefiniti.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)