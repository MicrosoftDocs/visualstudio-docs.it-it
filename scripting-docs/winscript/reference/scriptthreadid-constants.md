---
title: Costanti SCRIPTTHREADID | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc692716115ea0c205b1cfd982b189fffd54a9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptthreadid-constants"></a>Costanti SCRIPTTHREADID
Utilizzato per specificare il tipo di thread.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Costanti  
  
|Costante|Valore|Significato|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Il thread attualmente in esecuzione.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Il thread di base. vale a dire il thread in cui la creazione di script del motore è stata creata un'istanza.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Tutti i thread.|  
  
## <a name="remarks"></a>Note  
 Il `SCRIPTTHREADID` tipo viene utilizzato da `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, e `IActiveScript::InterruptScriptThread`, ma le costanti possono essere utilizzate esclusivamente `IActiveScript::GetScriptThreadState` e `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)