---
title: Enumerazione JsValueType | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsValueType
helpviewer_keywords:
- JsValueType enumeration
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4f61cf9118c19a0fc35e7505af422b812d0b43
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsvaluetype-enumeration"></a>Enumerazione JsValueType
Tipo JavaScript di JsValueRef.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## <a name="members"></a>Membri  
  
### <a name="values"></a>Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JsUndefined`|Il valore è il valore `undefined`.|  
|`JsNull`|Il valore è il valore `null`.|  
|`JsNumber`|Il valore è un valore numerico JavaScript.|  
|`JsString`|Il valore è un valore stringa JavaScript.|  
|`JsBoolean`|Il valore è un valore booleano JavaScript.|  
|`JsObject`|Il valore è un valore oggetto JavaScript.|  
|`JsFunction`|Il valore è un valore oggetto funzione JavaScript.|  
|`JsError`|Il valore è un valore oggetto errore JavaScript.|  
|`JsArray`|Il valore è un valore oggetto matrice JavaScript.|  
|`JsSymbol`|Il valore è un valore di simbolo JavaScript.<br /><br /> Questo valore di enumerazione è supportato solo in modalità Bordo|  
|`JsArrayBuffer`|Il valore è un valore oggetto `ArrayBuffer` JavaScript.<br /><br /> Questo valore di enumerazione è supportato solo in modalità Bordo|  
|`JsTypedArray`|Il valore è un valore oggetto matrice tipizzata JavaScript.<br /><br /> Questo valore di enumerazione è supportato solo in modalità Bordo|  
|`JsDataView`|Il valore è un valore oggetto `DataView` JavaScript.<br /><br /> Questo valore di enumerazione è supportato solo in modalità Bordo|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)