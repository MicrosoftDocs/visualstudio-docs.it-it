---
title: Enumerazione PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab542225e0238dbd40f90d9de66d43d0791e05e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>Enumerazione PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS
Flag che determinano un oggetto nell'heap a cui punta in una relazione di oggetto è un metodo getter o setter. Utilizzato nel [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) quando il valore PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS è specificato nel metodo il `enumFlags` parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Valore|Descrizione|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Questo oggetto nell'heap a cui fa riferimento a una relazione di oggetto non viene identificato come metodo di un getter o setter.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|L'oggetto heap a cui fa riferimento a una relazione di oggetto è un metodo di richiamo. Queste informazioni verranno archiviate nei 2 byte (16 bit) elevati del [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) campo.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|L'oggetto heap a cui fa riferimento a una relazione di oggetto è un metodo set. Queste informazioni verranno archiviate nei 2 byte (16 bit) elevati del `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` campo.|