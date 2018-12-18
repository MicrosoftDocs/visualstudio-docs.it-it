---
title: Enumerazione BREAKPOINT_STATE | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKPOINT_STATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKPOINT_STATE enumeration
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 881598b39625b02651a4d57456904db60ace80c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="breakpointstate-enumeration"></a>Enumerazione BREAKPOINT_STATE
Indica lo stato di un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|BREAKPOINT_DELETED|Il punto di interruzione non esiste più, ma sono ancora presenti riferimenti a esso.|  
|BREAKPOINT_DISABLED|Il punto di interruzione è presente ma è disabilitato.|  
|BREAKPOINT_ENABLED|Il punto di interruzione esiste ed è abilitato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)