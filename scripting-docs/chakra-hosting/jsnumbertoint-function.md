---
title: Funzione JsNumberToInt | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f24acb837fdf46694aa2370e2ccf1fe3c926ce19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsnumbertoint-function"></a>Funzione JsNumberToInt
Recupera il valore `int` di un valore numerico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `value`  
 Valore numerico da convertire in un valore `int`.  
  
 `intValue`  
 Valore `int`.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Questa funzione recupera il valore di un valore numerico e lo converte in un valore `int`. Avrà esito negativo con `JsErrorInvalidArgument` se il tipo del valore non è numerico.  
  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)