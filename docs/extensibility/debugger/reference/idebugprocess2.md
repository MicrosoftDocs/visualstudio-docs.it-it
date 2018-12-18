---
title: IDebugProcess2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2
helpviewer_keywords: IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 896448526f41514fb74b385f8605839908708305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2"></a>IDebugProcess2
Questa interfaccia rappresenta un processo in esecuzione su una porta. Se la porta è la porta locale, quindi `IDebugProcess2` in genere rappresenta un processo fisico del computer locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata da un fornitore di porta personalizzato per gestire i programmi come un gruppo. Questa interfaccia deve essere implementata dal fornitore porta.  
  
 Un motore di debug implementa questa interfaccia anche se supporta l'avvio di un programma tramite [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene chiamata principalmente dal gestore di sessione di debug (SDM) per interagire con un gruppo di programmi identificate in questo processo.  
  
 Chiamare [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) o [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) per ottenere questa interfaccia. Questa interfaccia viene inoltre restituita chiamando `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProcess2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ottiene una descrizione del processo.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera i programmi contenuti in questo processo.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ottiene il titolo, un nome descrittivo o un nome di file del processo.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ottiene l'istanza di questo processo è in esecuzione in un server di computer.|  
|[Terminare](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Termina il processo.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Collega al processo.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina se il SDM possibile disconnettere il processo.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Disconnette il debugger dal processo.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ottiene l'identificatore di processo di sistema.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Ottiene un identificatore univoco globale per questo processo.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [DEPRECATO]|Ottiene il nome della sessione che è il processo di debug.<br /><br /> [OBSOLETO. DEVE SEMPRE RESTITUIRE `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera i thread in esecuzione nel processo.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Richiede che il programma successivo esecuzione di codice in questo arresto del processo.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ottiene la porta è in esecuzione il processo.|  
  
## <a name="remarks"></a>Note  
 Un `IDebugProcess2` contiene uno o più [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfacce.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Avanti](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)