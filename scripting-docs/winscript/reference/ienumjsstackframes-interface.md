---
title: Interfaccia IEnumJsStackFrames | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12583f73c9f3977371ebd193716f2513fc0befc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ienumjsstackframes-interface"></a>Interfaccia IEnumJsStackFrames
Implementati dal debugger per fornire dello stack di rimozione per jscript9diag.dll per JavaScript.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Ottiene il numero di frame specificato.|  
|[Metodo IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Reimposta il frame dello stack nella posizione prima del primo elemento.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)