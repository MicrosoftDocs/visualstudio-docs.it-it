---
title: Funzione JsGetAndClearException | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetAndClearException
helpviewer_keywords:
- JsGetAndClearException function
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e7e4f89bac59aa776762586ab20fa831b5c24bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetandclearexception-function"></a>Funzione JsGetAndClearException
Restituisce l'eccezione che ha causato lo stato d'eccezione del runtime del contesto corrente e reimposta lo stato di eccezione per quel runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `exception`  
 Eccezione per il runtime del contesto corrente.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se il runtime del contesto corrente non si trova in uno stato di eccezione, questa API restituirà `JsErrorInvalidArgument`. Se il runtime è disabilitato, questo restituirà un'eccezione che indica che lo script è stato interrotto, ma non annullerà l'eccezione (l'eccezione verrà annullata se il runtime viene riabilitato usando `JsEnableRuntimeExecution`).  
  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)