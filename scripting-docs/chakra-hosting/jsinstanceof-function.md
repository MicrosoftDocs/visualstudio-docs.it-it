---
title: Funzione JsInstanceOf | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94399a62-b996-4fd2-82ce-1c26e7a4da08
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00b5018ae3d04e6bcb361b1c765df61e5855d553
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsinstanceof-function"></a>Funzione JsInstanceOf
Esegue il test dell'operatore "instanceof" JavaScript.  
  
## <a name="syntax"></a>Sintassi  
  
```  
JsInstanceOf(   
  _In_ JsValueRef object,  
  _In_ JsValueRef constructor,  
  _Out_ bool *result  
);  
  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Oggetto da testare.  
  
 `constructor`  
 Funzione del costruttore da usare per il test.  
  
 `result`  
 Indica se il valore di "object instanceof constructor" è true.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)