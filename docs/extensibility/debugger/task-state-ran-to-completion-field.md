---
title: Campo TASK_STATE_RAN_TO_COMPLETION | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: becc2087e9b956eb7305793fd41ff0ef4c5fdbcc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="taskstaterantocompletion-field"></a>Campo TASK_STATE_RAN_TO_COMPLETION
L'esecuzione dell'attività è stata completata correttamente.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## <a name="remarks"></a>Note  
 Se il [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene questo valore, il <xref:System.Threading.Tasks.Task.Status%2A> restituisce proprietà <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe dell'attività](../../extensibility/debugger/task-class-internal-members.md)