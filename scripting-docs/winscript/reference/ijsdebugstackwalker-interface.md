---
title: Interfaccia IJsDebugStackWalker | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbea11bf1188d148818ea8a082bceec76c704c2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugstackwalker-interface"></a>Interfaccia IJsDebugStackWalker
Rappresenta un walker dello stack per un thread specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugStackWalker::GetNext](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Ottiene il frame successivo.|  
  
## <a name="remarks"></a>Note  
 È possibile creare walkers stack solo la destinazione è stato arrestato, mentre una volta ripreso nuovamente il processo di destinazione non sono valida.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)