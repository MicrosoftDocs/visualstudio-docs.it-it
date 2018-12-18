---
title: Interfaccia IActiveScriptProfilerCallback2 | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dc9fcd8ca4afec0fb474c0f3a7317b608c7c9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2-interface"></a>Interfaccia IActiveScriptProfilerCallback2
Fornisce metodi che vengono utilizzati dal motore di scripting per notificare a un oggetto del profiler quando si verificano eventi di Strumentazione gestione Windows (DOM, Document Object Model). Questa interfaccia viene implementata dall'oggetto del profiler.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Notifica all'oggetto del profiler che il motore di script deve essere eseguita una chiamata di funzione DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifica al profiler di oggetto che lo script del motore terminata l'esecuzione di una chiamata di funzione DOM.|  
  
## <a name="remarks"></a>Note  
 Il `IActiveScriptProfilerCallback2` interfaccia rilasciata inizialmente con Internet Explorer 9.  
  
 Notifica delle chiamate di funzione che non sono chiamate nel DOM è offerta dal [interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Per aggiungere la possibilità di avviare e interrompere la profilatura quando uno script è in esecuzione, chiamare i metodi seguenti. Usando questi metodi, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si avvia o interrompere la profilatura.  
>   
>  -   Chiamare [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) per notificare al profiler che sia stato avviato a profilatura.  
> -   Chiamare [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) per notificare al profiler che è appena profilatura verrà interrotta.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)