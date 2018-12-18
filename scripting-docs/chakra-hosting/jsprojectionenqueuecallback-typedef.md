---
title: Typedef JsProjectionEnqueueCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bda4a3a80edac38ab2c3885c2256cdf9d03eb8c1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsprojectionenqueuecallback-typedef"></a>Typedef JsProjectionEnqueueCallback
Callback dell'applicazione che viene chiamato da JsRT quando un'API di proiezione viene completata su un thread diverso rispetto a quello originale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `jsCallback`  
 Callback da richiamare sul thread originale.  
  
 `jsContext`  
 Contesto dell'applicazione.  
  
 `callbackState`  
 Contesto JsRT che deve essere passato in `jsCallback`.  
  
## <a name="remarks"></a>Note  
 Per ricevere i callback, è necessario chiamare JsSetProjectionEnqueueCallback.  
  
 Questa API è supportata solo in modalità Edge.  
  
## <a name="requirements"></a>Requisiti  
 jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)