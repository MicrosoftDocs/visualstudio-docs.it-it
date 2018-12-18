---
title: IRemoteDebugApplication::ResumeFromBreakPoint | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5da5fdbaaf74f463161f1a98bbad7d4d147b418d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Continua un'applicazione che si trova in un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `prptFocus`  
 [in] Per l'esecuzione di istruzioni modalità, il thread che deve essere interessati dalla modalità di esecuzione di istruzioni.  
  
 `bra`  
 [in] L'azione da eseguire dopo il ripristino dell'applicazione.  
  
 `era`  
 [in] L'azione da intraprendere nel caso in cui l'applicazione è stata interrotta a causa di un errore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo continua a un'applicazione che si trova in un punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Enumerazione ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)