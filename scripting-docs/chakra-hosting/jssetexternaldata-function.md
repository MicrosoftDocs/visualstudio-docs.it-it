---
title: Funzione JsSetExternalData | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetExternalData
helpviewer_keywords:
- JsSetExternalData function
ms.assetid: 94e0ad34-67d7-4f7f-88a3-3b057ef5e4b9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf7e21cded2b4b1bdb50fef53fc8d298434a14eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jssetexternaldata-function"></a>Funzione JsSetExternalData
Imposta i dati esterni in un oggetto esterno.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetExternalData(  
   _In_ JsValueRef object,  
   _In_opt_ void *externalData  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Oggetto esterno.  
  
 `externalData`  
 Dati esterni archiviati nell'oggetto. Può essere null se nessun dato esterno è archiviato nell'oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)