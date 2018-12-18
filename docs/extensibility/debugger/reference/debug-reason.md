---
title: DEBUG_REASON | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_REASON
helpviewer_keywords: DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fda733db5a70d88d5029c4001c632c234d32a823
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugreason"></a>DEBUG_REASON
Specifica i motivi per cui il processo è stato avviato per il debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 DEBUG_REASON_ERROR  
 Si è verificato un errore non specifico (utilizzato come una condizione predefinita quando nessuno degli altri motivi di adattamento).  
  
 DEBUG_REASON_USER_LAUNCHED  
 Il processo è stato avviato su richiesta dell'utente.  
  
 DEBUG_REASON_USER_ATTACHED  
 Il processo già in esecuzione è stato collegato dall'utente.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 Il processo è stato associato automaticamente al quando è stata avviata.  
  
 DEBUG_REASON_CAUSALITY  
 Il processo è stato avviato a causa di un *Just-In-Time* evento di debug (JIT).  
  
## <a name="remarks"></a>Note  
 Restituito dal [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)