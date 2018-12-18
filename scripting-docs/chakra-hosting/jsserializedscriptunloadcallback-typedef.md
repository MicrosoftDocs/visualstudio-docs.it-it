---
title: Typedef JsSerializedScriptUnloadCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f485d31367f189231d354c653c8e58cc8656eb9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptunloadcallback-typedef"></a>typedef JsSerializedScriptUnloadCallback
Chiamato dal runtime quando viene terminato con tutte le risorse correlate all'esecuzione di script.     Il chiamante deve liberare l'origine se caricata, il codice byte e il contesto in questo momento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `sourceContext`  
 Contesto passato a `JsParseSerializedScriptWithCallback` o a `JsRunSerializedScriptWithCallback`.  
  
## <a name="remarks"></a>Note  
  
> [!WARNING]
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)