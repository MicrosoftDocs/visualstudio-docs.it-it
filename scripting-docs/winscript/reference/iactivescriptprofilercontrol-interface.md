---
title: Interfaccia IActiveScriptProfilerControl | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d598302ae78ca0b2a1e7c1f94c949800378a2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol-interface"></a>Interfaccia IActiveScriptProfilerControl
Implementato dal motore di script che supporta la profilatura. In genere, un oggetto che implementa il `IActiveScriptProfilerControl` implementa inoltre il [IActiveScript](../../winscript/reference/iactivescript.md) interfaccia. In questo caso, è possibile ottenere un handle per il `IActiveScriptProfilerControl` interfaccia chiamando il `IUnknown::QueryInterface` metodo sull'oggetto. L'interfaccia fornisce i metodi necessari per arrestare e avviare la profilatura sul motore di script.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Avvia il profiling nel motore di scripting.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Imposta il profiler maschera eventi nel motore di scripting.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Arresta la profilatura sul motore di scripting.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)