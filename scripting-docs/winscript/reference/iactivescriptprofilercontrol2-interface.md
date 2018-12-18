---
title: Interfaccia IActiveScriptProfilerControl2 | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bc0dfa31b37a6bf99427c8eddfe2bd038da9b9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2-interface"></a>Interfaccia IActiveScriptProfilerControl2
Fornisce metodi che aggiungono la possibilità di avviare o interrompere la profilatura quando uno script è in esecuzione.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Notifica al profiler che è stata avviata l'analisi su tutti i motori di script applicabili. In questo modo è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si avvia la profilatura.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Notifica al profiler che si desidera interrompere la profilatura in tutti i motori di script applicabili. In questo modo è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si arresta la profilatura.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)