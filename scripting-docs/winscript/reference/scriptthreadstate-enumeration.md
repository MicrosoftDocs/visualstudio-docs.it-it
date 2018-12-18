---
title: Enumerazione SCRIPTTHREADSTATE | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e18cc6f5f2afb1dcea6835983f69f6a6f7b9280
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptthreadstate-enumeration"></a>Enumerazione SCRIPTTHREADSTATE
Specifica lo stato di un thread in un motore di script. Questa enumerazione viene utilizzata per la [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Thread specificato è attualmente non manutenzione di un evento tramite script, testo dello script di elaborazione eseguita immediatamente, o esecuzione di una macro di script.|  
|SCRIPTTHREADSTATE_RUNNING|Thread specificato è attivamente la manutenzione di un evento tramite script, testo dello script di elaborazione eseguita immediatamente, o esecuzione di una macro di script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)