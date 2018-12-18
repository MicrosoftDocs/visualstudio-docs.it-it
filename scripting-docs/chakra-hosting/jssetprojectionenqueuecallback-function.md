---
title: Funzione JsSetProjectionEnqueueCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abdc575c5066ade4a700a0c88e09e3476a65366
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jssetprojectionenqueuecallback-function"></a>Funzione JsSetProjectionEnqueueCallback
Imposta il callback da usare per richiamare un completamento di proiezione nel thread richiesto dai chiamanti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### <a name="parameters"></a>Parametri  
 `projectionEnqueueContext`  
 Callback che verrà richiamato ogni volta che si verifica un completamento di proiezione su un thread in background.  
  
 `callbackState`  
 Contesto dell'applicazione fornito a `projectionEnqueueContext`.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Richiede un contesto di script attivo.  
  
 La chiamata deve provenire da un diverso apartment COM o da un thread differente nello stesso attributo MTA.  
  
 Questa API è supportata solo in modalità Edge.  
  
> [!CAUTION]
>  PInvoke non è attualmente supportato per questa API.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)