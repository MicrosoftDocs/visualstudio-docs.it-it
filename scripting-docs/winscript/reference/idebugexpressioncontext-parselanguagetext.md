---
title: IDebugExpressionContext::ParseLanguageText | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e455768b7d38096c64ab61f2b36aeba871ddf0bc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Crea un'espressione di debug per il testo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrCode`  
 [in] Fornisce il testo dell'espressione o una o più istruzioni.  
  
 `nRadix`  
 [in] Radice da utilizzare.  
  
 `pstrDelimiter`  
 [in] Il delimitatore di fine-di--blocco di script. Quando `pstrCode` viene analizzata da un flusso di testo, l'host in genere viene utilizzato un delimitatore, ad esempio due virgolette singole ("), per rilevare la fine del blocco di script. Questo parametro specifica il delimitatore che l'host utilizzato, consentendo il motore di script fornire alcuni condizionale primitivi pre-elaborazione (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) utilizzati dal motore scripting questa informazioni dipendono dal motore di script. Impostare questo parametro su `NULL` se l'host non ha utilizzato un delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwFlags`  
 [in] Combinazione dei flag di testo di debug seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica che il testo è un'espressione anziché un'istruzione. Questo flag può influenzare le modalità in cui il testo viene analizzato da alcuni linguaggi.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Se un valore restituito è disponibile, e verrà utilizzato dal chiamante.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Non consentire gli effetti collaterali. Se questo flag è impostato, la valutazione dell'espressione deve modificare nessuno stato di runtime.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Consente i punti di interruzione durante la valutazione del testo. Se questo flag non è stato impostato durante la valutazione del testo vengono ignorati i punti di interruzione.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Consente di segnalazioni di errore durante la valutazione del testo. Se questo flag non è quindi gli errori non vengono segnalati all'host durante la valutazione.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica l'espressione da valutare per un contesto di codice, anziché eseguire l'espressione stessa|  
  
 `ppe`  
 [out] Restituisce l'espressione di debug per il testo specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo crea un'espressione di debug per il testo specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)