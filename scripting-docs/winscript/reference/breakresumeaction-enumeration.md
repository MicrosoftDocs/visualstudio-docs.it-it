---
title: Enumerazione BREAKRESUMEACTION | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="breakresumeaction-enumeration"></a>Enumerazione BREAKRESUMEACTION
Descrive come proseguire da un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Interrompe l'applicazione.|  
|BREAKRESUMEACTION_CONTINUE|Continua l'esecuzione.|  
|BREAKRESUMEACTION_STEP_INTO|Esegue l'istruzione di una routine.|  
|BREAKRESUMEACTION_STEP_OVER|Ignora una routine.|  
|BREAKRESUMEACTION_STEP_OUT|Esce dalla routine corrente.|  
|BREAKRESUMEACTION_IGNORE|Continua l'esecuzione con lo stato.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Passa al documento successivo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)