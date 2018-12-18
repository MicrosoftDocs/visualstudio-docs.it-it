---
title: Typedef JsNativeFunction | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cf475dd6a17434ea132647b7d8bde833f0de9e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsnativefunction-typedef"></a>Typedef JsNativeFunction
Callback di funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 callee  
 Oggetto `Function` che rappresenta la funzione richiamata.  
  
 isConstructCall  
 Indica se si tratta di una chiamata normale o di una "nuova" chiamata.  
  
 arguments  
 Argomenti della chiamata.  
  
 argumentCount  
 Numero di argomenti.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Risultato della chiamata, se presente.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)