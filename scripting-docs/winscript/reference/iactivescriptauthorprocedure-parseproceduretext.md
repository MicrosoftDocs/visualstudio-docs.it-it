---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9c4a1ba03a8498dbaa857dc5dbabba8914e54a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analizza una routine di codice, aggiunge il testo della stored procedure codice allo script di creazione del motore e crea un `IScriptEntry` oggetto che corrisponde al codice procedura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCode`  
 [in] Il testo dello script da analizzare.  
  
 `pszFormalParams`  
 [in] L'indirizzo dei nomi di parametro formale per la procedura. I nomi di parametro devono essere separati dai delimitatori appropriati per lo script del motore di creazione. I nomi non devono essere racchiusi tra parentesi.  
  
 `pszProcedureName`  
 [in] L'indirizzo del nome della routine da analizzare.  
  
 `pszItemName`  
 [in] L'indirizzo del buffer che contiene il nome dell'elemento associato il `IScriptEntry` oggetto.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore di fine-di--blocco di script. Quando `pszCode` viene analizzata da un flusso di testo, l'host Usa in genere un delimitatore (ad esempio due virgolette singole), per individuare la fine del blocco di script. Impostare questo parametro su NULL se non è disponibile alcun delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwCookie`  
 [in] Un valore definito dall'applicazione che viene associato alla nuova `IScriptEntry` oggetto.  
  
 `dwFlags`  
 [in] Non usato.  
  
 `pdispFor`  
 [in] Non usato.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Corrente [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore non implementa questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)