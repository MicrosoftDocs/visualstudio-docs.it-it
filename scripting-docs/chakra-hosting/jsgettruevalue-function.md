---
title: Funzione JsGetTrueValue | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetTrueValue
helpviewer_keywords:
- JsGetTrueValue function
ms.assetid: c2a56d48-344b-492b-90b8-f570710f8310
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61d4dfdb7d4e2b7c2c26e57e58f9f3d501e436c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsgettruevalue-function"></a>Funzione JsGetTrueValue
Ottiene il valore di `true` nel contesto script corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsGetTrueValue(  
   _Out_ JsValueRef *trueValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `trueValue`  
 Valore `true`.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)