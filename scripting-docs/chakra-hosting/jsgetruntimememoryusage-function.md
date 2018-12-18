---
title: Funzione JsGetRuntimeMemoryUsage | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetRuntimeMemoryUsage
helpviewer_keywords:
- JsGetRuntimeMemoryUsage function
ms.assetid: b9bd4146-bfbc-4cb1-a0e9-a0ded7fb09bd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3519e4395ab5b3b7bbc5186c56775bdef9b12ecf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetruntimememoryusage-function"></a>Funzione JsGetRuntimeMemoryUsage
Ottiene l'utilizzo della memoria corrente per un runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryUsage(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryUsage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `runtime`  
 Runtime di cui viene recuperato l'utilizzo della memoria.  
  
 `memoryUsage`  
 Utilizzo della memoria corrente del runtime, in byte.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'utilizzo della memoria può essere sempre recuperato, indipendentemente dal fatto che il runtime sia attivo in un altro thread.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)