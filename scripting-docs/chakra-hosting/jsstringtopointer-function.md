---
title: Funzione JsStringToPointer | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsStringToPointer
helpviewer_keywords:
- JsStringToPointer function
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ff84f929833941fed9a709497dc615189c39386
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsstringtopointer-function"></a>Funzione JsStringToPointer
Recupera il puntatore di stringa di un valore di stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `value`  
 Valore di stringa da convertire in un puntatore di stringa.  
  
 `stringValue`  
 Puntatore di stringa.  
  
 `stringLength`  
 Lunghezza della stringa.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questa funzione recupera il puntatore di stringa di un valore di stringa. Non riesce con `JsErrorInvalidArgument` se il valore non è di tipo stringa. La durata della stringa restituita sarà uguale a quella del valore da cui proviene. Tuttavia, il puntatore di stringa non viene considerato un riferimento al valore (quindi verrà escluso dalla raccolta).  
  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)