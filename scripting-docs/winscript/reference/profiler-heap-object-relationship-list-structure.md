---
title: Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 46ca87ea-5b0f-437d-a33f-b2d9a457e036
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fdad752587869fbdd1edfa325ddc1282cfa3a95
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectrelationshiplist-structure"></a>Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST
Rappresenta un elenco di relazioni che appartengono a un oggetto heap.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_RELATIONSHIP elements[];} PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Tipo|Descrizione|  
|------------|----------|-----------------|  
|count|UINT|Il numero di relazioni di un oggetto heap.|  
|elementi|[Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Le relazioni di un oggetto heap.|