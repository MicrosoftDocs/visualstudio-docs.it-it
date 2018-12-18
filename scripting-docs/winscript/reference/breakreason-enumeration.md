---
title: Enumerazione BREAKREASON | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1baa8b627df50db33cbd86302ce06e80c1cf34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="breakreason-enumeration"></a>Enumerazione BREAKREASON
Indica la causa dell'interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|BREAKREASON_STEP|Il motore del linguaggio è in modalità di esecuzione di istruzioni.|  
|BREAKREASON_BREAKPOINT|Il motore del linguaggio ha rilevato un punto di interruzione esplicito.|  
|BREAKREASON_DEBUGGER_BLOCK|Il motore del linguaggio ha rilevato un blocco di debugger in un altro thread.|  
|BREAKREASON_HOST_INITIATED|L'host ha richiesto un'interruzione.|  
|BREAKREASON_LANGUAGE_INITIATED|Il motore del linguaggio ha richiesto un'interruzione.|  
|BREAKREASON_DEBUGGER_HALT|Il debugger IDE ha richiesto un'interruzione.|  
|BREAKREASON_ERROR|Un errore di esecuzione ha causato l'interruzione.|  
|BREAKREASON_JIT|Causato dall'avvio del debug JIT.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)