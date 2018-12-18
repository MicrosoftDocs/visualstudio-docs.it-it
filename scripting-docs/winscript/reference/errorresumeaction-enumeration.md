---
title: Enumerazione ERRORRESUMEACTION | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 914c1d7aa4d2935ea94322ebd257f4135d79e9c0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="errorresumeaction-enumeration"></a>Enumerazione ERRORRESUMEACTION
Descrive come proseguire a seguito di un errore di runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Esegue nuovamente l'istruzione che ha generato l'errore.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Consente di gestire l'errore il motore del linguaggio.|  
|ERRORRESUMEACTION_SkipErrorStatement|Riprende l'esecuzione del codice che segue l'istruzione che ha generato l'errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)