---
title: Funzione JsSetRuntimeMemoryLimit | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryLimit
helpviewer_keywords:
- JsSetRuntimeMemoryLimit function
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 587eb369e6971c7527177624ccf5baf839246cf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimememorylimit-function"></a>Funzione JsSetRuntimeMemoryLimit
Imposta il limite di memoria corrente per il runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `runtime`  
 Il runtime il cui limite di memoria viene impostato.  
  
 `memoryLimit`  
 Il nuovo limite di memoria del runtime, in byte oppure -1 per non limitare la memoria.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un limite di memoria comporta che una qualsiasi operazione che supera il limite fallisce restituendo un errore "memoria insufficiente". Impostare il limite di memoria del runtime a -1 indica che il runtime non ha limite di memoria. I nuovi runtime, come impostazione predefinita, non hanno limiti di memoria. Se il nuovo limite di memoria supera l'utilizzo corrente, la chiamata avrà esito positivo e tutte le future allocazioni in questo runtime avranno esito negativo fino a che l'utilizzo della memoria del runtime non scenderà sotto il limite.  
  
 Il limite di memoria del runtime può essere sempre impostato, indipendentemente dal fatto che il runtime sia attivo in un altro thread.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)