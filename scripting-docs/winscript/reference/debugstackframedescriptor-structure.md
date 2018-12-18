---
title: Struttura DebugStackFrameDescriptor | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="debugstackframedescriptor-structure"></a>Struttura DebugStackFrameDescriptor
Enumera gli stack frame e unisce l'output da più enumeratori sullo stesso thread.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Membri  
 `pdsf`  
 L'oggetto stack frame.  
  
 `dwMin`  
 Rappresentazione in forma di dipendenti dal computer dell'intervallo inferiore di indirizzi fisici associati a questo stack frame.  
  
 `dwLim`  
 Rappresentazione dell'intervallo di indirizzi fisici associati a questo stack frame superiore dipendenti dal computer.  
  
 `fFinal`  
 Flag che indica che il frame è in elaborazione.  
  
 `punkFinal`  
 Se questo parametro non è `NULL`, l'enumeratore corrente unione deve essere arrestato e deve essere avviato uno nuovo. L'oggetto indica la modalità avviare la nuova enumerazione.  
  
## <a name="remarks"></a>Note  
 Il gestore di debug del processo Usa questa struttura per ordinare gli stack frame da più moduli di script. Per convenzione, gli stack di aumento delle dimensioni verso il basso. Di conseguenza, su architetture qualora crescere stack, gli indirizzi devono essere completati a coppie.  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)