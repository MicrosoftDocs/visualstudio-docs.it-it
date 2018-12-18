---
title: Enumerazione APPBREAKFLAGS | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 126dcd704a60b591b71913f2e8e739de35c14636
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="appbreakflags-enumeration"></a>Enumerazione APPBREAKFLAGS
Indicano lo stato corrente del debug delle applicazioni e dei thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Valore|Descrizione|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Motore del linguaggio deve interrompere immediatamente tutti i thread con BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Motore del linguaggio è presente un'interruzione immediatamente con BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Motore del linguaggio deve interrompere il debug passo a passo thread con BREAKREASON_STEP immediatamente.|  
|APPBREAKFLAG_NESTED|0x00020000|L'applicazione è in esecuzione annidata in un punto di interruzione.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Il debugger è l'esecuzione di istruzioni a livello di origine.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Il debugger è l'esecuzione di istruzioni a livello di codice di byte.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Il debugger è l'esecuzione di istruzioni a livello di computer.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Maschera di separazione dei tipi di passaggi.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Un punto di interruzione è in corso.|  
  
## <a name="remarks"></a>Note  
 Alcuni flag di specifica che i motori di linguaggio devono interrompersi alla successiva opportunità, mentre altri flag di specificare la modalità di esecuzione del debugger.  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture, enumerazioni e costanti del Debugger dello Script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)