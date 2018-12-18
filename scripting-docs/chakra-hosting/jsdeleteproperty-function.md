---
title: Funzione JsDeleteProperty | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsDeleteProperty
helpviewer_keywords:
- JsDeleteProperty function
ms.assetid: 0f6ac6a7-3576-42f5-98d0-1c06542c8149
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60a6da027fe128d91770bbf2d299d5d23de6d3eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsdeleteproperty-function"></a>Funzione JsDeleteProperty
Elimina una proprietà dell'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsDeleteProperty(  
   _In_ JsValueRef object,  
   _In_ JsPropertyIdRef propertyId,  
   _In_ bool useStrictRules,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Oggetto che contiene la proprietà.  
  
 `propertyId`  
 ID della proprietà.  
  
 `useStrictRules`  
 L'insieme di proprietà deve seguire le regole della modalità strict.  
  
 `result`  
 Indica se la proprietà è stata eliminata.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)