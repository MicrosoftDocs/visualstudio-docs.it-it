---
title: Typedef JsProjectionCallbackContext | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7548dc14ab4b3dddc1633a1ba948aba564d8438a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsprojectioncallbackcontext-typedef"></a>Typedef JsProjectionCallbackContext
Contesto passato nel callback dell'applicazione, JsProjectionEnqueueCallback, da JsRT e quindi passato nuovamente a JsRT nel callback specificato, `JsProjectionCallback`, dall'applicazione nel thread corretto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## <a name="remarks"></a>Note  
 Per ricevere callback, è necessario chiamare `JsSetProjectionEnqueueCallback` .  
  
 Questa API è supportata solo in modalità Edge.  
  
## <a name="requirements"></a>Requisiti  
 jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)