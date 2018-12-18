---
title: 'Metodo iactivescriptprofilercontrol5:: Enumheap2 | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c493acdb2843877c506d9d84e145a79ac2d60d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>Metodo IActiveScriptProfilerControl5::EnumHeap2
Restituisce un'interfaccia ([interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) che può essere utilizzato per scorrere gli oggetti dell'heap di Garbage Collection nel contesto del motore di script associati.  
  
 È possibile chiamare questo metodo in una modalità di debug o la modalità di rilascio. Questo metodo deve essere chiamato quando il thread dell'interfaccia utente è inattivo. Dopo che è stato chiamato il metodo, nessuna operazione devono essere eseguita in motore di script, ad eccezione [metodo iactivescriptprofilerheapenum:: Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) fino a quando non [metodo iactivescriptprofilerheapenum:: Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)restituisce S_FALSE o [interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) puntatore a interfaccia viene rilasciato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametri  
 enumFlags  
 Valore che specifica se viene esposta informazioni aggiuntive su un oggetto a cui fa riferimento a una relazione di oggetto. Informazioni aggiuntive possono indicare se l'oggetto a cui puntata è un metodo getter o setter. Per altre informazioni, vedere [enumerazione PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Restituisce il [interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|L'enumerazione dell'heap completata.|  
|`E_OUTOFMEMORY`|Non è disponibile memoria sufficiente eseguire l'enumerazione dell'heap.|  
|`E_FAIL`|Si è verificato un errore interno.|