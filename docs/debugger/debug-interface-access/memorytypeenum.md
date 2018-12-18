---
title: MemoryTypeEnum | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e6281f52d7c7388cbe4f683d3690cb68b6358d67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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