---
title: IActiveScriptProfilerCallback::ScriptCompiled | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ea1823087b323f2acc9b87edfce48bbe9f924bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Notifica al profiler di oggetto che lo script del motore compilato uno script. Questo metodo viene chiamato per ogni script che viene compilato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametri  
 `scriptId`  
 [in] ID univoco dello script che è stato compilato. Questo ID viene assegnato dal motore di scripting.  
  
 `type`  
 [in] Il tipo di script che è stato compilato. I valori vengono definiti [enumerazione PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] Se disponibile, un puntatore a un `IUnknown` interfaccia che il profiler deve eseguire una query per un [interfaccia IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) puntatore. In caso contrario, il valore è null.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di scripting.  
  
## <a name="remarks"></a>Note  
 Il motore di script è possibile fornire il contesto del documento solo se supportato dall'host.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)