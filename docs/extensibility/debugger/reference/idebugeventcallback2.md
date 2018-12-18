---
title: IDebugEventCallback2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEventCallback2
helpviewer_keywords: IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 165f973fa9139f281211e6b01167b3d7044166df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Questa interfaccia viene utilizzata dal motore di debug (DE) per inviare gli eventi di debug al gestore di sessione di debug (SDM).  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]implementa questa interfaccia per la ricezione di eventi da un motore di debug.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Un motore di debug riceve questa interfaccia in genere quando si chiama il SDM [collegamento](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [collegamento](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un motore di debug invia eventi per il SDM chiamando [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugEventCallback2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Invia una notifica di eventi per il SDM di debug.|  
  
## <a name="remarks"></a>Note  
 Sebbene [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) specificare che accettano un `IDebugEventCallback2` interfaccia, non è il caso e il puntatore di interfaccia sarà sempre un valore null. In alternativa, è necessario utilizzare il motore di debug di `IDebugEventCallback2` interfaccia ricevuto nella chiamata a [Connetti](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Connetti](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Se un pacchetto implementa [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) nel codice gestito, è consigliabile che <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> essere richiamato su varie interfacce che vengono passate a [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)