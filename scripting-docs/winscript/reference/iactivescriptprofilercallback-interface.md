---
title: Interfaccia IActiveScriptProfilerCallback | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc4b9d4e3b1f83a37e64e3a85387fd378d3ca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback-interface"></a>Interfaccia IActiveScriptProfilerCallback
Fornisce metodi che vengono utilizzati dal motore di scripting per notificare a un oggetto del profiler quando si verificano eventi. Questa interfaccia viene implementata dall'oggetto del profiler.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Chiamato per inizializzare l'oggetto del profiler ogni volta che l'analisi viene avviata in un motore di scripting.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Chiamata eseguita per liberare e rilasciare l'oggetto profiler ogni volta che l'analisi è stato arrestato nel motore di script.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifica al profiler di oggetto che lo script del motore di script di compilazione.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifica al profiler di oggetto che lo script del motore ha rilevato una funzione durante la compilazione di uno script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Notifica all'oggetto del profiler che il motore di script sta per essere eseguita una chiamata di funzione che non è una chiamata nel modello oggetto documento (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifica al profiler di oggetto che il motore di script terminato l'esecuzione di una funzione chiamata che non è una chiamata nel DOM.|  
  
## <a name="remarks"></a>Note  
 La notifica delle chiamate di funzione nel modello oggetto documento (DOM) viene fornita dal [interfaccia IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Per aggiungere la possibilità di avviare e interrompere la profilatura quando uno script è in esecuzione, chiamare i metodi seguenti. Usando questi metodi, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si avvia o interrompere la profilatura.  
>   
>  -   Chiamare [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) per notificare al profiler che sia stato avviato a profilatura.  
> -   Chiamare [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) per notificare al profiler che è appena profilatura verrà interrotta.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)