---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd26ab1cf36378c0f037d78a3c079c58e004006d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Notifica al profiler di oggetto che lo script del motore terminata l'esecuzione di una chiamata di funzione di Strumentazione gestione Windows (DOM, Document Object Model).  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parametri  
 `pwszFunctionName`  
 [in] Il nome della funzione che il motore di script termina l'esecuzione.  
  
 `scriptType`  
 [in] Il tipo della funzione. Per le descrizioni dei valori validi, vedere [enumerazione PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di scripting.  
  
## <a name="remarks"></a>Note  
 Per le chiamate di DOM, il motore di script chiama questo metodo anziché chiamare [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Si tratta a causa dell'elevato numero di metodi univoci e le proprietà nel DOM.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [Interfaccia IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)