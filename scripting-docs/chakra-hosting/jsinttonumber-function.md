---
title: Funzione JsIntToNumber | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1393c4ac-7189-4e9c-8e54-b0e041c22112
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e7ad87dcbe802173be863754dbb5f87c71af149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsinttonumber-function"></a>Funzione JsIntToNumber
Crea un valore numerico da un valore `int`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsIntToNumber(  
   _In_ int intValue,  
   _Out_ JsValueRef *value  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `intValue`  
 Valore `int` da convertire in valore numerico.  
  
 `value`  
 Nuovo valore numerico.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)