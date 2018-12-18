---
title: Typedef JsProjectionCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80d1c64f04f44a8560c25935fba2a48905a73260
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsprojectioncallback-typedef"></a>Typedef JsProjectionCallback
Callback JsRT che deve essere chiamato con il contesto passato a `JsProjectionEnqueueCallback` nel thread corretto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `jsContext`  
 Per ricevere callback, è necessario chiamare `JsSetProjectionEnqueueCallback` .  
  
## <a name="remarks"></a>Note  
 Questa API è supportata solo in modalità Edge.  
  
## <a name="requirements"></a>Requisiti  
 jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)