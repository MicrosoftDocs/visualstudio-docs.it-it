---
title: Funzione JsValueToVariant | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsValueToVariant
helpviewer_keywords:
- JsValueToVariant function
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2beb0a72a8e19d38d80ab8bf29ce0478ba7f481f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsvaluetovariant-function"></a>Funzione JsValueToVariant
Inizializza l'oggetto passato in `VARIANT` come proiezione di un valore JavaScript.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Valore JavaScript nel progetto come `VARIANT`.  
  
 `variant`  
 Puntatore a uno struct `VARIANT` che verrà inizializzato come proiezione.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 La proiezione `VARIANT` può essere utilizzata dai client di automazione COM per effettuare una chiamata nell'oggetto JavaScript proiettato.  
  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)