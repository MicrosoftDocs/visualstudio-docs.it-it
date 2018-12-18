---
title: 'Metodo iactivescriptprofilerheapenum:: Getoptionalinfo | Documenti Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6ad237f2feb173408e895984dab7e7455004d16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>Metodo IActiveScriptProfilerHeapEnum::GetOptionalInfo
Ottiene le informazioni facoltative sull'oggetto specificato (dal set di heap oggetti restituiti dal [metodo iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Non è necessario liberare la memoria restituita assegnata agli oggetti restituiti. Chiamare invece il [metodo iactivescriptprofilerheapenum:: Freeobjectandoptionalinfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Parametri  
 `heapObject`  
 Il [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) per cui restituire le informazioni.  
  
 `celt`  
 Il numero di [struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) strutture da restituire.  
  
 `optionalInfo`  
 [out] Matrice di [struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) strutture per l'oggetto specificato.  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT.