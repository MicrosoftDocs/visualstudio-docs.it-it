---
title: Funzione JsCreateExternalArrayBuffer | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95459f9a9ff676f47d56ed584ad44a30f24fd4cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jscreateexternalarraybuffer-function"></a>Funzione JsCreateExternalArrayBuffer
Crea un oggetto `ArrayBuffer` JavaScript per accedere alla memoria esterna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### <a name="parameters"></a>Parametri  
 `data`  
 Puntatore alla memoria esterna.  
  
 `byteLength`  
 Numero di byte nella memoria esterna.  
  
 `finalizeCallback`  
 Callback per quando l'oggetto viene completato. Può essere Null.  
  
 `callbackState`  
 Stato fornito dall'utente restituito per finalizzare il callback.  
  
 `result`  
 Nuovo oggetto `ArrayBuffer` .  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)