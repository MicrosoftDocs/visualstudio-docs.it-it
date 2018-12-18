---
title: Struttura JS_NATIVE_FRAME | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7e93041a6dec767cb3bb11382abfb562068c925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsnativeframe-structure"></a>Struttura JS_NATIVE_FRAME
Rappresenta uno stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>Membri  
 `InstructionOffset`  
 Puntatore dell'istruzione.  
  
 `ReturnOffset`  
 Indirizzo del mittente.  
  
 `FrameOffset`  
 Puntatore ai frame.  
  
 `StackOffset`  
 Puntatore dello stack.  
  
## <a name="remarks"></a>Note  
 Il `JS_NATIVE_FRAME` struct viene utilizzato da `IJsStackFrameEnumerator`.  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)