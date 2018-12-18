---
title: Funzione JsGetPropertyNameFromId | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetPropertyNameFromId
helpviewer_keywords:
- JsGetPropertyNameFromId function
ms.assetid: b4ca442c-573d-4bc3-adf7-1b8d48480b3a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f14851a52f4e6de1e2702ad11eab20bf448a048
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetpropertynamefromid-function"></a>Funzione JsGetPropertyNameFromId
Ottiene il nome associato all'ID proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyNameFromId(  
   _In_ JsPropertyIdRef propertyId,  
   _Outptr_result_z_ const wchar_t **name  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `propertyId`  
 ID proprietà di cui ottenere il nome.  
  
 `name`  
 Nome associato all'ID proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
 Il buffer restituito è valido finché resta attivo il runtime e non può essere usato dopo l'eliminazione del runtime.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)