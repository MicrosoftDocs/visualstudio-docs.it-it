---
title: 'Metodo iactivescriptprofilerheapenum:: Next | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3927743a1de1d3048537327aebd24a847a7d22e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenumnext-method"></a>Metodo IActiveScriptProfilerHeapEnum::Next
Ottiene l'oggetto successivo o gli oggetti nel set di oggetti dell'heap di [metodo iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Next (    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,     [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 Il numero di oggetti da restituire.  
  
 `heapObjects`  
 [out] Alla successiva [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) strutture.  
  
 `pceltFetched`  
 [out] Il numero di oggetti restituiti,  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT.