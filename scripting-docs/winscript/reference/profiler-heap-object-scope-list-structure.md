---
title: Struttura PROFILER_HEAP_OBJECT_SCOPE_LIST | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67f0972faee11e15bd5d0e9a219e439df49d9672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectscopelist-structure"></a>Struttura PROFILER_HEAP_OBJECT_SCOPE_LIST
Questa struttura è associata solo gli oggetti funzione. L'elenco di ambito rappresenta la chiusura per la funzione come un elenco di ambiti in cui ogni ambito è un oggetto dell'heap con un elenco di proprietà associata che rappresenta le variabili in ogni ambito specifico. In alcuni casi, i nomi di oggetti nell'ambito potrebbe non essere disponibile e solo il relativo indice nell'elenco di proprietà è disponibile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Tipo|Descrizione|  
|------------|----------|-----------------|  
|count|UINT|Il numero di ambiti|  
|scopes|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Matrice di ambiti.|