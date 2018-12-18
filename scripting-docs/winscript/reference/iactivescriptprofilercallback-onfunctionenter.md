---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9af9dc5ce1f4cb0eb5c328c90c20184111afd9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Notifica all'oggetto del profiler che il motore di script sta per essere eseguita una chiamata di funzione che non è una chiamata nel modello oggetto documento (DOM).  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnFunctionEnter(  
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
 Per le chiamate di DOM, chiama il motore di script [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) anziché `IActiveScriptProfilerCallback::OnFunctionEnter`. Si tratta a causa dell'elevato numero di metodi univoci e le proprietà nel DOM.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)