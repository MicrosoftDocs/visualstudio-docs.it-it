---
title: IActiveScriptProfilerCallback::OnFunctionExit | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57a3343c7e3747c48a4c43a1c1ac17fe6502aee3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Notifica al profiler di oggetto che il motore di script terminato l'esecuzione di una funzione chiamata che non è una chiamata nel modello oggetto documento (DOM).  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parametri  
 `scriptId`  
 [in] ID univoco dello script che fa parte della funzione. Questo ID viene assegnato dal motore di scripting.  
  
 `functionId`  
 [in] ID univoco della funzione. Questo ID viene assegnato dal motore di scripting.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di scripting.  
  
## <a name="remarks"></a>Note  
 Per le chiamate di DOM, chiama il motore di script [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) anziché `IActiveScriptProfilerCallback::OnFunctionExit`. Si tratta a causa dell'elevato numero di metodi univoci e le proprietà nel DOM.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)