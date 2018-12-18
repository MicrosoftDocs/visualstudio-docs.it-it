---
title: Funzione JsHasException | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsHasException
helpviewer_keywords: JsHasException function
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32334f4b8787bebaffb9553fcdd40f85334462cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jshasexception-function"></a>Funzione JsHasException
Determina se il runtime del contesto corrente è in uno stato di eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `hasException`  
 Se il runtime del contesto corrente è in stato di eccezione.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se una chiamata al runtime genera un'eccezione (in seguito all'esecuzione di uno script o a causa di un evento come un errore di conversione), il runtime viene impostato su uno "stato di eccezione". Tutte le chiamate a un contesto creato dal runtime (tranne le API di eccezione) non riusciranno con `JsErrorInExceptionState` finché l'eccezione non viene eliminata.  
  
 Se il runtime del contesto corrente è in stato di eccezione quando un callback torna nel motore, il motore genera di nuovo l'eccezione automaticamente.  
  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)