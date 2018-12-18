---
title: IActiveScriptProfilerCallback::Initialize | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.Initialize
apilocation: scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82e599ae94f422352706a0ec6cd9387bfa6799f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
Chiamato per inizializzare l'oggetto del profiler ogni volta che l'analisi viene avviata in un motore di scripting.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwContext`  
 [in] Un valore a 4 byte che viene passato a [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Se il metodo non è possibile inizializzare l'oggetto del profiler, deve restituire un HRESULT di errore per notificare al motore di scripting. In questo caso, il motore di script deve chiamare direttamente [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), passando il parametro HRESULT e quindi rilasciare l'oggetto del profiler.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)