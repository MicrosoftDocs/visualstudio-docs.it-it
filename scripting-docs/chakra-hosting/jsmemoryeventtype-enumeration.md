---
title: Enumerazione JsMemoryEventType | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsMemoryEventType
helpviewer_keywords: JsMemoryEventType enumeration
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef39008ba84337cebdc9613db17cc9fbdfc8aa79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsmemoryeventtype-enumeration"></a>Enumerazione JsMemoryEventType
Tipo di evento di callback di allocazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum JsMemoryEventType;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="values"></a>Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JsMemoryAllocate`|Indica una richiesta di allocazione di memoria.|  
|`JsMemoryFailure`|Indica un evento di allocazione non superato.|  
|`JsMemoryFree`|Indica un evento di liberazione di memoria.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)