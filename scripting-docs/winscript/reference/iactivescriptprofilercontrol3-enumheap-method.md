---
title: 'Metodo iactivescriptprofilercontrol3:: Enumheap | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d6fc79a9d6d35e35181c3505e07af2d9a1962c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>Metodo IActiveScriptProfilerControl3::EnumHeap
Restituisce un'interfaccia ([interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) che può essere utilizzato per scorrere gli oggetti dell'heap di Garbage Collection nel contesto del motore di script associati.  
  
 È possibile chiamare questo metodo in una modalità di debug o la modalità di rilascio. Questo metodo deve essere chiamato quando il thread dell'interfaccia utente è inattivo. Dopo che è stato chiamato il metodo, nessuna operazione devono essere eseguita in motore di script, ad eccezione [metodo iactivescriptprofilerheapenum:: Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) fino a quando non [metodo iactivescriptprofilerheapenum:: Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)restituisce S_FALSE o [interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) puntatore a interfaccia viene rilasciato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametri  
 ppEnum  
 [out] Restituisce il [interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT.