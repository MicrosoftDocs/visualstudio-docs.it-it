---
title: IActiveScriptProfilerCallback2::OnFunctionEnterByName | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea74d9e9e00485c86d26bb01c486992f85ffeb8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Notifica all'oggetto del profiler che il motore di script verrà eseguito una chiamata di funzione di Strumentazione gestione Windows (DOM, Document Object Model).  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pwszFunctionName`  
 [in] Il nome della funzione che il motore di script da eseguire.  
  
 `scriptType`  
 [in] Il tipo della funzione. Per le descrizioni dei valori validi, vedere [enumerazione PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di scripting.  
  
## <a name="remarks"></a>Note  
 Per le chiamate di DOM, il motore di script chiama questo metodo anziché chiamare [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Si tratta a causa dell'elevato numero di metodi univoci e le proprietà nel DOM.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [Interfaccia IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)