---
title: Interfaccia IActiveScriptProfilerHeapEnum | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4761e8c7d4cc9c3372c7906e1503b8dbd059ca33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenum-interface"></a>Interfaccia IActiveScriptProfilerHeapEnum
Un iteratore sull'heap oggetti associati a un motore di script, di raccolta di [metodo iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## <a name="methods"></a>Metodi  
 [Metodo IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 Ottiene l'oggetto successivo o gli oggetti nel set di oggetti degli heap raccolti dal [metodo iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [Metodo IActiveScriptProfilerHeapEnum::GetOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 Ottiene le informazioni facoltative sull'oggetto specificato nel set di oggetti degli heap raccolti dal [metodo iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [Metodo IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 Libera l'oggetto specificato [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) strutture e i relativi [struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) elementi.  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 Restituisce i nomi di stringa corrispondente a [tipo PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md) valori...