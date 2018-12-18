---
title: Funzione JsSetException | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSetException
helpviewer_keywords: JsSetException function
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d8fce71f14dedea02e1809fb72281f575f60604
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jssetexception-function"></a>Funzione JsSetException
Imposta il runtime del contesto corrente su uno stato di eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `exception`  
 Eccezione JavaScript da impostare per il runtime del contesto corrente.  
  
## <a name="return-value"></a>Valore restituito  
 `JsNoError` se il motore era impostato su uno stato di eccezione, in caso contrario un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se il runtime del contesto corrente si trova già in uno stato di eccezione, questa API restituirà `JsErrorInExceptionState`.  
  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)