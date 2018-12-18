---
title: IActiveScriptAuthor::GetScriptTextAttributes | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aa96623b4356f0a3d17c8b2631840953dac2d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Restituisce gli attributi di testo per un blocco di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCode`  
 [in, size_is (`cch`)] il testo del blocco di script. È la stringa a terminazione null.  
  
 `cch`  
 [in] La dimensione utilizzata per la `pszCode` e `pattr` parametri.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore di fine-script. Quando `pszCode` viene analizzata da un flusso di testo, l'host Usa in genere un delimitatore (ad esempio due virgolette singole), per individuare la fine dello scriptlet. Impostare questo parametro su NULL se non è disponibile alcun delimitatore per identificare la fine del blocco di script.  
  
 `dwFlags`  
 [in] I flag che sono associati gli attributi di testo del blocco di script. Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identificare gli identificatori che includono l'attributo SOURCETEXT_ATTR_IDENTIFIER e identificare gli operatori punto che dispongono dell'attributo SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identificare l'oggetto corrente con l'attributo SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identificare il testo contenuto e commento stringa che contiene l'attributo SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] le informazioni di colore per il codice del blocco di script.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)