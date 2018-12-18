---
title: Metodo SetNotificationForWaitCompletion | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a005ee7d624604dd716042bd839b48b7a367dd48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setnotificationforwaitcompletion-method"></a>Metodo SetNotificationForWaitCompletion
Imposta o Cancella il bit di stato TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parametri  
 `enabled`  
  
 `true` Per impostare il bit; `false` a non impostato il bit.  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
 Il debugger imposta questo bit per uscire il corpo di un metodo asincrono. Se `enabled` è `true`, questo metodo deve essere chiamato solo su un'attività che non è ancora stata completata. Se `enabled` è `false`, questo metodo può essere chiamato per le attività completate. In entrambi i casi deve essere utilizzato solo per le attività di tipo pianificato.  
  
## <a name="requirements"></a>Requisiti  
  
## <a name="see-also"></a>Vedere anche  
 [Classe dell'attività](../../extensibility/debugger/task-class-internal-members.md)