---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5abd4ee4237991714bfe3d8ba21b083f1a1920cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Notifica al profiler che è stata avviata l'analisi su tutti i motori di script applicabili. Tramite questo metodo, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si avvia la profilatura.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parametri  
 Il metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Impossibile avviare la profilatura.|  
|`S_FALSE`|Profilatura è stata avviata quando uno script non è in esecuzione.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilatura non è abilitata. Non è stato impostato alcun callback.|  
|`E_OUTOFMEMORY`|Non è possibile ottenere lo stack di chiamate a causa di una condizione di memoria insufficiente.|  
  
## <a name="remarks"></a>Note  
 La chiamata `IActiveScriptProfilerControl2::CompleteProfilerStart` assicura che vengano inviati gli eventi per le funzioni già nello stack di chiamate. Questo metodo deve essere chiamato dopo la profilatura viene avviato nel alcun motore di scripting della scheda corrente. Il metodo può essere chiamato per un motore di script.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Interfaccia IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)