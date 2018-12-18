---
title: Enumerazione JsDebugReadMemoryFlags | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7efb5170bf0314e95b1acded39a897c2236a29ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Enumerazione JsDebugReadMemoryFlags
Flag per specificare il comportamento durante la lettura della memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="values"></a>Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indica che il chiamante richiede l'operazione di lettura avranno esito positivo se solo parte della memoria di lettura è stato completato. Se questo valore è impostato, verrà generato un errore di E_JsDEBUG_INVALID_MEMORY_ADDRESS solo se 'Address' non è valido. Se questo flag è deselezionato, verrà generato un errore E_JsDEBUG_INVALID_MEMORY_ADDRESS se qualsiasi parte della memoria richiesta è illeggibile.|  
|`None`|Indica che il chiamante richiede il comportamento predefinito per ReadMemory.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)