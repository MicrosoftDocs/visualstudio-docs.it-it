---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78078cd874be1d7d3d169be2d3d70e65866be3fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Notifica al profiler che si desidera interrompere la profilatura in tutti i motori di script applicabili. Tramite questo metodo, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si arresta la profilatura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parametri  
 Il metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Impossibile avviare analisi.|  
|`S_FALSE`|Profilatura interrotta quando uno script non è in esecuzione.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilatura non è abilitata.|  
  
## <a name="remarks"></a>Note  
 La chiamata `IActiveScriptProfilerControl2::PrepareProfilerStop` assicura che vengano inviati gli eventi per le funzioni nello stack di chiamate. Questo metodo deve essere chiamato prima di interrompere la profilatura sul alcun motore di scripting della scheda corrente. Il metodo può essere chiamato per un motore di script.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Interfaccia IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)