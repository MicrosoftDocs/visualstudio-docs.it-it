---
title: Classe - membri interni Task | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 161572ece44f3a9f07c9eb40638ca98170e3a86c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="task-class---internal-members"></a>Classe Task - membri interni
In questo argomento vengono descritti i membri interni del <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe che consentono di implementare un debugger personalizzato. Per informazioni generali su questa classe, vedere il <xref:System.Threading.Tasks.Task> argomento di riferimento.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Membri  
  
### <a name="methods"></a>Metodi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Imposta o Cancella il bit di stato TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|  
|[Metodo NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metodo segnaposto utilizzato come destinazione del punto di interruzione dal debugger.|  
  
### <a name="fields"></a>Campi  
  
|nome|Descrizione|  
|----------|-----------------|  
|[m_action viene](../../extensibility/debugger/m-action-field.md)|Delegato che rappresenta il codice da eseguire nel <xref:System.Threading.Tasks.Task> oggetto.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Archivia le proprietà aggiuntive del <xref:System.Threading.Tasks.Task> oggetto.|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Il campo sottostante per il <xref:System.Threading.Tasks.Task?displayProperty=fullName> proprietà padre.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Archivia le informazioni sullo stato corrente del <xref:System.Threading.Tasks.Task> oggetto.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Oggetto che rappresenta i dati che verranno utilizzati dall'azione.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Il campo sottostante per il <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> proprietà.|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|L'identificatore successivo disponibile per un <xref:System.Threading.Tasks.Task> oggetto.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica che l'attività è stata annullata prima ha raggiunto lo stato di esecuzione o che l'attività ha confermato il relativo annullamento e completata senza eccezioni.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica che l'attività è in esecuzione.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica che l'attività completata a causa di un'eccezione non gestita.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica che l'attività esecuzione completata correttamente.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica che l'attività ha terminato l'esecuzione del delegato e in modo implicito attende il completamento delle attività figlio collegate.|  
  
## <a name="remarks"></a>Note  
 I seguenti metodi interni sono utili per un motore del debugger perché contrassegnate all'ingresso di <xref:System.Threading.Tasks.Task> esecuzione di codice:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)