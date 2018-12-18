---
title: Typedef JsBackgroundWorkItemCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c4281ae1abf1df07d4b6374b6989377c66c1fd7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsbackgroundworkitemcallback-typedef"></a>Typedef JsBackgroundWorkItemCallback
Callback di un elemento di lavoro in background.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 callbackData  
 Argomento di dati passato al servizio thread.  
  
## <a name="remarks"></a>Note  
 Questo argomento viene passato al servizio thread dell'host (se fornito) per consentire all'host di richiamare il callback dell'elemento di lavoro sul thread in background scelto.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)