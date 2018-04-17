---
title: MemoryTypeEnum | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 92eaaa63f276d9107dfa3155eb85d52884d3157c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Specifica il tipo di memoria per l'accesso.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 `MemTypeCode`  
 Accede solo il codice della memoria.  
  
 `MemTypeData`  
 Accede a dati o dello stack di memoria.  
  
 `MemTypeStack`  
 Accessi solo la memoria dello stack.  
  
 `MemTypeAny`  
 Accede a qualsiasi tipo di memoria.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono passati per la [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) metodo per limitare l'accesso a tipi diversi di memoria.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)