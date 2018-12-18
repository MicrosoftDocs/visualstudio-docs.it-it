---
title: Panoramica della profilatura di script ActiveX | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9413e8b6e6db0c81eb1853c24506d20c8d06f3e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-profiling-overview"></a>Panoramica della profilatura di script ActiveX
Le [interfacce di profilatura di script ActiveX](../winscript/reference/active-script-profiler-interfaces.md) abilitano la profilatura di un motore di script. La profilatura di script ActiveX è costituita dalle parti seguenti:  
  
-   Modulo di gestione del linguaggio  
  
-   Host  
  
-   Profiler  
  
## <a name="language-engine"></a>Modulo di gestione del linguaggio  
 Il modulo di gestione del linguaggio esegue lo script. Specifica metodi che consentono la profilatura del codice di script durante l'esecuzione. Quando la profilatura è abilitata, il modulo di gestione del linguaggio accetta come argomento l'identificatore di classe (CLSID) dell'oggetto COM profiler. Quindi crea un'istanza dell'oggetto COM profiler e chiama il profiler quando si verificano diversi eventi.  
  
 Il modulo di gestione del linguaggio implementa l'[interfaccia IActiveScriptProfilerControl](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  Il runtime del linguaggio [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] verifica la variabile di ambiente JS_PROFILER al momento della creazione per determinare se la profilatura deve essere abilitata. Se la variabile è impostata sull'identificatore di classe (CLSID) del profiler, il runtime del linguaggio crea un'istanza dell'oggetto COM profiler usando il valore della variabile per determinare quale profiler creare.  
  
## <a name="host"></a>Host  
 L'host crea il modulo di gestione del linguaggio e rende disponibili al modulo gli script da eseguire. Uno smart host specifica anche il contesto di documento che un debugger o un profiler può usare per offrire informazioni più complete durante il debug o la profilatura.  
  
## <a name="profiler"></a>Profiler  
 Il profiler riceve chiamate dal modulo di gestione del linguaggio quando si verificano diversi eventi. Il profiler deve essere registrato come oggetto COM e implementare l'interfaccia [IActiveScriptProfilerCallback](../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../winscript/reference/active-script-profiler-interfaces.md)