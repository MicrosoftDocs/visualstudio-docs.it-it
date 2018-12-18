---
title: Enumerazione JS_PROPERTY_ATTRIBUTES | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JS_PROPERTY_ATTRIBUTES
apilocation: jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed034ef6fc134838058b75534f1b5c17c1ec2e3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jspropertyattributes-enumeration"></a>Enumerazione JS_PROPERTY_ATTRIBUTES
Indica gli attributi di una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Membri  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|La proprietà non contiene attributi.|  
|`JS_PROPERTY_HAS_CHILDREN`|La proprietà contiene figli.|  
|`JS_PROPERTY_FAKE`|La proprietà rappresenta un finto nodo, ad esempio "[Methods]".|  
|`JS_PROPERTY_METHOD`|La proprietà è un metodo.|  
|`JS_PROPERTY_READONLY`|La proprietà è in sola lettura.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|La proprietà è un puntatore a un oggetto WinRT nativo.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)