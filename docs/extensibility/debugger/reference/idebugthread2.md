---
title: IDebugThread2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d93744e55a3e516a131e772fd2df09da5ec23168
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2"></a>IDebugThread2
Questa interfaccia rappresenta un thread in esecuzione in un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un thread di esecuzione in un programma singolo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) per ottenere l'interfaccia che rappresenta il thread attualmente attivo.  
  
 Questa interfaccia viene anche utilizzata per creare una richiesta di punto di interruzione (vedere [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).  
  
 Questa interfaccia viene restituita anche durante la risoluzione di un punto di interruzione associato o errore (vedere [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) e [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugThread2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Recupera un elenco di stack frame per il thread.|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Ottiene il nome del thread.|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Imposta il nome del thread.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Ottiene il programma in cui un thread è in esecuzione.|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Determina se l'istruzione successiva è possibile impostare per il contesto di determinato stack frame e il codice.|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Imposta l'istruzione successiva nel contesto del determinato stack frame e il codice.|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Ottiene l'identificatore del thread di sistema.|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Sospende un thread.|  
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Riprende un thread.|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Ottiene le proprietà che descrivono un thread.|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Ottiene il thread logico associato a questo thread fisico.|  
  
## <a name="remarks"></a>Note  
 Poiché un singolo thread fisici possono essere eseguiti in più programmi, più `IDebugThread2` da più di un programma può rappresentare lo stesso thread fisico.  
  
 Quando si verifica un punto di interruzione o un'eccezione, viene inviato un evento chiamando [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Uno degli argomenti di questo metodo è un `IDebugThread2` interfaccia che rappresenta il thread corrente. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) viene utilizzata per ottenere il [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia per lo stack frame corrente.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)