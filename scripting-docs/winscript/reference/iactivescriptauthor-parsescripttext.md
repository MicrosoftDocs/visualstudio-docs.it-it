---
title: IActiveScriptAuthor::ParseScriptText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e81d96ae817b2117f12cb56fd59759f4c2b849
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analizza il testo dello script, aggiunge il testo dello script di creazione del motore e crea un `IScriptEntry` oggetto che corrisponde al blocco di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCode`  
 [in] Il testo dello script da analizzare.  
  
 `pszItemName`  
 [in] L'indirizzo del buffer che contiene il nome dell'elemento associato al blocco di script.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore di fine-di--blocco di script. Quando `pszCode` viene analizzata da un flusso di testo, l'host Usa in genere un delimitatore (ad esempio due virgolette singole), per individuare la fine del blocco di script. Impostare questo parametro su NULL se non è disponibile alcun delimitatore per identificare la fine del blocco di script.  
  
 `dwCookie`  
 [in] Un valore definito dall'applicazione che viene associato alla nuova `IScriptEntry` oggetto.  
  
 `dwFlags`  
 [in] Non usato.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)