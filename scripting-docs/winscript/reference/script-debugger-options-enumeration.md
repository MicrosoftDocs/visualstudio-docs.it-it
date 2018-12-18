---
title: Enumerazione SCRIPT_DEBUGGER_OPTIONS | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54b910562670104f0fb5679f2b09780afcd17751
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptdebuggeroptions-enumeration"></a>Enumerazione SCRIPT_DEBUGGER_OPTIONS
Indica un set di opzioni e/o funzionalità che si applicano al debugger collegato. Utilizzato [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) e [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Queste costanti vengono implementate da PDM v di 10.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Valore|Descrizione|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Non sono impostate opzioni.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Indica che l'esecuzione dello script deve generare eventi BREAKREASON_ERROR quando viene generata un'eccezione. Questa opzione può essere impostata dal debugger, o dal codice utente tramite `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Indica che il debugger collegato supporta web worker.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)