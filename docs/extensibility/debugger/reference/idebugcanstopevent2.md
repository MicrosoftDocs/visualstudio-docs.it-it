---
title: IDebugCanStopEvent2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2
helpviewer_keywords: IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 59e601e828fd3dad1487925c649972efc7b019a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Questa interfaccia viene utilizzata per chiedere di gestore di sessione di debug (SDM) se si desidera arrestare in corrispondenza della posizione di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per supportare l'esecuzione passo passo il codice sorgente. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia (utilizza il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia).  
  
 L'implementazione di questa interfaccia deve comunicare la chiamata del SDM di [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) al motore di debug. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al messaggio del motore di debug thread di gestione o l'oggetto che implementa questa interfaccia può contenere un riferimento al motore di debug e richiamare il motore di debug con il flag passato `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania può inviare questo metodo ogni volta che la Germania viene chiesto di continuare l'esecuzione e il DE è avanzamento tramite codice. Questo evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback fornita dal suo SDM quando è collegato al programma sottoposto a debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugCanStopEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ottiene il motivo per questo evento.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Specifica se il programma in corso il debug deve essere arrestato in corrispondenza di questo evento (e invia un evento che descrive il motivo dell'arresto) o semplicemente continuare l'esecuzione.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ottiene il contesto del documento che descrive il percorso di questo evento.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ottiene il contesto del codice che descrive il percorso di questo evento.|  
  
## <a name="remarks"></a>Note  
 Se i passi di utente in una funzione e il DE rileva che non esiste alcuna informazione di debug o le informazioni di debug presenti, ma la Germania non sa se il codice sorgente può essere visualizzato per tale percorso, la Germania invia questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)