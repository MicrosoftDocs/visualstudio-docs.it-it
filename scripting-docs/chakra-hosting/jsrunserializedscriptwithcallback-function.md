---
title: Funzione JsRunSerializedScriptWithCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce51c9473100e71831dd53cc6572d9740790ffa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsrunserializedscriptwithcallback-function"></a>Funzione JsRunSerializedScriptWithCallback
Esegue uno script serializzato.     Fornisce la possibilità di eseguire caricamento lazy del codice script solo se/quando è necessario.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_opt_ JsValueRef *result  
);  
  
```  
  
#### <a name="parameters"></a>Parametri  
 `scriptLoadCallback`  
 Callback chiamato quando il codice sorgente dello script deve essere caricato.  
  
 `scriptUnloadCallback`  
 Callback chiamato quando lo script serializzato e il codice sorgente non sono più necessari.  
  
 `buffer`  
 Script serializzato.  
  
 `sourceContext`  
 Cookie che identifica lo script che può essere usato dai contesti di script sottoponibili a debug.     Questo contesto verrà passato in scriptLoadCallback e scriptUnloadCallback.  
  
 `sourceUrl`  
 Percorso di origine dello script.  
  
 `result`  
 Risultato dell'esecuzione dello script, se disponibile. Questo parametro può essere null.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
  
> [!NOTE]
>  Questa API non è ancora disponibile per le app di Windows Store.  
  
 Richiede un contesto di script attivo.  
  
 Il runtime manterrà il buffer finché tutte le istanze di qualsiasi funzione creata dal buffer non vengono sottoposte a Garbage Collection.  Verrà quindi chiamato scriptUnloadCallback per informare il chiamante che è possibile eseguire il rilascio.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)