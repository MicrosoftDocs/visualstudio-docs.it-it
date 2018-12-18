---
title: Funzione JsSetRuntimeBeforeCollectCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeBeforeCollectCallback
helpviewer_keywords:
- JsSetRuntimeBeforeCollectCallback function
ms.assetid: 7b2fb911-6007-4ed9-a307-66cefe590ea4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 469b33a324f67d17bd6f5156da7cce169b98c663
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimebeforecollectcallback-function"></a>Funzione JsSetRuntimeBeforeCollectCallback
Imposta una funzione di callback che viene chiamata dal runtime prima dell'operazione di Garbage Collection.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeBeforeCollectCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsBeforeCollectCallback beforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `runtime`  
 Runtime per il quale registrare il callback di allocazione.  
  
 `callbackState`  
 Stato fornito dall'utente che verrà passato al callback.  
  
 `beforeCollectCallback`  
 Funzione di callback impostata.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il callback viene richiamato sul thread in esecuzione nel runtime corrente, quindi l'esecuzione viene bloccata fino al completamento della chiamata.  
  
 Il callback può essere usato dagli host per preparare per la procedura di Garbage Collection. Ad esempio, rilasciando i riferimenti non necessari agli oggetti Chakra.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)