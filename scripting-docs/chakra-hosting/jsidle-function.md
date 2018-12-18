---
title: Funzione JsIdle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsIdle
helpviewer_keywords:
- JsIdle function
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddffd4f37c0e10985a2dbca26558d8a94b21b2f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsidle-function"></a>Funzione JsIdle
Indica al runtime di eseguire eventuali elaborazioni durante l'inattività che devono essere svolte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `nextIdleTick`  
 Ciclo di sistema successivo in cui sarà presente ulteriore lavoro da svolgere durante l'inattività. Può essere null. Restituisce il numero massimo di cicli se non c'è lavoro imminente da svolgere durante l'inattività.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se l'elaborazione durante l'inattività è stata abilitata per il runtime corrente, la chiamata di `JsIdle` informa il runtime corrente che l'host è inattivo e che il runtime può eseguire attività di pulizia della memoria.  
  
 `JsIdle` può anche restituire il numero di cicli di sistema fino a quando non sarà presente ulteriore lavoro che deve essere svolto dal runtime durante l'inattività. Se si chiama `JsIdle` prima che sia passato questo numero di cicli, l'operazione non funziona.  
  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)