---
title: Enumerazione PROFILER_HEAP_ENUM_FLAGS | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a7a27f4d9d7f834b07a2db5ba8433b63222a3b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapenumflags-enumeration"></a>Enumerazione PROFILER_HEAP_ENUM_FLAGS
Flag indicante se viene esposta informazioni aggiuntive su un oggetto nell'heap a cui fa riferimento a una relazione di oggetto. Utilizzato nel [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Valore|Descrizione|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|Questo oggetto heap non espone informazioni aggiuntive su una relazione tra oggetti. Questo oggetto heap si comporta esattamente come [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|Questo oggetto heap espone informazioni o meno un oggetto a cui fa riferimento a una relazione di oggetto è un metodo getter o setter. Queste informazioni verranno archiviate nei 2 byte (16 bit) elevati del [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) campo tra il [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) valori di enumerazione.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|Questo oggetto heap viene utilizzato per visualizzare correttamente la sottostringa.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|Questo oggetto heap viene utilizzato per visualizzare correttamente la sottostringa.|