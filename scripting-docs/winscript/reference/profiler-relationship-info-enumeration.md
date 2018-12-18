---
title: Enumerazione profiler_info_object_flags | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f01ca5e001d45907af70b46b6dc362e8ae0b2044
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="profilerrelationshipinfo-enumeration"></a>Enumerazione PROFILER_INFO_OBJECT_FLAGS
Rappresenta le informazioni sull'oggetto nella relazione. Utilizzato [struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Valore|Descrizione|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|L'oggetto è un numero.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|L'oggetto è una stringa.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|L'oggetto è un oggetto heap.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|L'oggetto è esterno, ovvero, non sull'heap di garbage collection.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|L'oggetto è un tipo BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|L'oggetto è una SOTTOSTRINGA.|