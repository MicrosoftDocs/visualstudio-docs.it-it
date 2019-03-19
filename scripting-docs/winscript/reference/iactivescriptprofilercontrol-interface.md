---
title: Interfaccia IActiveScriptProfilerControl | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 86f4fb8dea97930f717800a14a27740b76eb6c2e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160758"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Interfaccia IActiveScriptProfilerControl
Implementato dal motore di script che supporta la profilatura. In genere, un oggetto che implementa il `IActiveScriptProfilerControl` implementa anche il [IActiveScript](../../winscript/reference/iactivescript.md) interfaccia. In questo caso, è possibile ottenere un handle per il `IActiveScriptProfilerControl` interfaccia chiamando il `IUnknown::QueryInterface` metodo sull'oggetto. L'interfaccia fornisce i metodi necessari per arrestare e avviare la profilatura sul motore di script.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Avvia la profilatura sul motore di scripting.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Imposta il profiler maschera evento nel motore di scripting.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Arresta la profilatura sul motore di scripting.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)