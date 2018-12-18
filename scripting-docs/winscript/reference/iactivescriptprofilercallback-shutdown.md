---
title: IActiveScriptProfilerCallback::Shutdown | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec47cd5f581c36abb60b662983c6d806a4732f47
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Chiamata eseguita per informare l'oggetto del profiler, ogni volta che l'analisi è stato arrestato nel motore di script. In questo modo, l'oggetto del profiler può chiamare le routine di pulizia, se necessario. Questo metodo viene chiamato anche dal motore di script quando il motore di script è in corso l'arresto o quando una chiamata a [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) ha esito negativo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parametri  
 `hrReason`  
 [in] Il motivo dell'arresto. Se il motore di script è in corso l'arresto, `S_OK` viene passato. Se la chiamata a [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) restituisce un HRESULT di errore, viene passato il valore HRESULT. In caso contrario, questo valore viene recuperato da [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di scripting.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)