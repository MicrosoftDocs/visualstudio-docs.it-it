---
title: StackFrameTypeEnum | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 329661e857859a1f6452506ba2984ac962bf4ff2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Specifica il tipo di frame dello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Elementi  
 `FrameTypeFPO`  
 Puntatore ai frame omessi. Informazioni FPO disponibili.  
  
 `FrameTypeTrap`  
 Frame di Trap kernel.  
  
 `FrameTypeTSS`  
 Frame di Trap kernel.  
  
 `FrameTypeStandard`  
 Frame dello stack EBP standard.  
  
 `FrameTypeFrameData`  
 Puntatore ai frame omessi. Informazioni frame di dati disponibili.  
  
 `FrameTypeUnknown`  
 Frame che non dispone di eventuali informazioni di debug.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono restituiti da una chiamata al [idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)