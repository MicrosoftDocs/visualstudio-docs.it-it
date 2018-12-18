---
title: Script ActiveX Profiler costanti, enumerazioni e strutture | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a37f64b14d0d732e48de66bb5268d47c95426937
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Costanti, enumerazioni e strutture del profiler di script ActiveX
Le enumerazioni seguenti vengono utilizzate da interfacce attive del Profiler dello Script.  
  
## <a name="constants-enumerations-and-structures"></a>Costanti, enumerazioni e strutture  
  
|Costanti|Descrizione|  
|---------------|-----------------|  
|[Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|L'indirizzo esterno del profiler. Utilizzato [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) e [struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|L'ID dell'oggetto heap. Utilizzato [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)[struttura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)e [Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Tipo PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|L'ID del nome dell'oggetto heap. Utilizzato [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Enumerazioni|Descrizione|  
|------------------|-----------------|  
|[Enumerazione PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md)|Indica i tipi di eventi che devono eseguire il profiling.|  
|[Enumerazione PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Flag indicante se viene esposta informazioni aggiuntive su un oggetto nell'heap a cui fa riferimento a una relazione di oggetto. Utilizzato nel [metodo iactivescriptprofilercontrol5:: Enumheap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Enumerazione PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Flag che rappresentano informazioni di base sull'oggetto heap. Utilizzato nel [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Enumerazione PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Rappresenta tipi diversi di informazioni facoltative. Utilizzato [struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Enumerazione PROFILER_RELATIONSHIP_INFO](../../winscript/reference/profiler-relationship-info-enumeration.md)|Rappresenta le informazioni sull'oggetto nella relazione. Utilizzato [struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Enumerazione PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md)|Specifica il tipo di script.|  
  
|Strutture|Descrizione|  
|----------------|-----------------|  
|[Struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)|Rappresenta gli oggetti degli heap raccolti da [metodo iactivescriptprofilercontrol3:: Enumheap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Rappresenta informazioni facoltative sugli oggetti degli heap.|  
|[Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Rappresenta una relazione di un oggetto heap.|  
|[Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Rappresenta un elenco di relazioni che appartengono a un oggetto heap.|  
|[Struttura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Questa struttura è associata solo gli oggetti funzione. L'elenco di ambito rappresenta la chiusura per la funzione come un elenco di ambiti in cui ogni ambito è un oggetto dell'heap con un elenco di proprietà associata che rappresenta le variabili in ogni ambito specifico. In alcuni casi, i nomi degli oggetti in tale ambito potrebbero non essere disponibili, solo i relativi ID.|  
|[Struttura PROFILER_PROPERTY_TYPE_SUBSTRING_INFO](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Rappresenta le informazioni relative al tipo della sottostringa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)