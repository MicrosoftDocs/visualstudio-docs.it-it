---
title: Funzione JsGetRuntimeMemoryLimit | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetRuntimeMemoryLimit
helpviewer_keywords:
- JsGetRuntimeMemoryLimit function
ms.assetid: ed81ca60-99fd-46b0-89ae-f6ac07926904
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6373e166ff4efe6bc8c5a33d203d60647c4be9b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetruntimememorylimit-function"></a>Funzione JsGetRuntimeMemoryLimit
Ottiene il limite di memoria corrente per un runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryLimit  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `runtime`  
 Il runtime il cui limite di memoria viene richiamato.  
  
 `memoryLimit`  
 Il limite di memoria corrente del runtime, in byte, oppure -1 se non è stato impostato alcun limite.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il limite della memoria di un runtime può essere sempre recuperato, indipendentemente dal fatto che il runtime sia attivo in un altro thread.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)