---
title: 'Metodo iactivescriptprofilercallback3:: Setwebworkerid | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>Metodo IActiveScriptProfilerCallback3::SetWebWorkerId
Notifica al profiler sull'ID di lavoro da utilizzare per questa sessione di profilatura. Se la funzione non è in esecuzione nel contesto della pagina, non viene richiamato questo metodo. Il valore di `webWorkerId` viene incrementata di 1 per ogni thread di lavoro, a partire da 1. I valori di ID non devono essere stabile, oltre a una sessione e corrisponde solo all'ordine in cui sono stati creati i processi di lavoro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parametri  
 `webWorkerId`  
 L'ID del web worker.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di scripting.