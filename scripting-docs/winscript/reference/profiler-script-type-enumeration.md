---
title: Enumerazione PROFILER_SCRIPT_TYPE | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PROFILER_SCRIPT_TYPE
apilocation: scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279969ec0b50f705e39d2e29e700adc1e833ead3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="profilerscripttype-enumeration"></a>Enumerazione PROFILER_SCRIPT_TYPE
Specifica il tipo di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Specifica il codice di script definiti dall'utente.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Specifica il codice di script che viene generato in modo dinamico durante l'esecuzione.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Specifica il tipo di script per gli oggetti definiti dal motore di script e funzioni native.|  
|PROFILER_SCRIPT_TYPE_DOM|Specifica una chiamata nel servizio Replica file (DOM, Document Object Model) di Internet Explorer, ad esempio, una chiamata al `document.getElementById` metodo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Script ActiveX Profiler costanti, enumerazioni e strutture](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)