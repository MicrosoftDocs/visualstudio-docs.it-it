---
title: IDebugBreakpointRequest2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03403a09ea5cd66839bf31fe5c690262fd55f3a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Questa interfaccia rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Gestore di sessione di debug (SDM) in genere implementa questa interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Il motore di debug (DE) riceve questa interfaccia tramite una chiamata a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) per creare un punto di interruzione in sospeso. Una chiamata a [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) questa interfaccia può recuperare la Germania.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugBreakpointRequest2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Ottiene il tipo di posizione del punto di interruzione della richiesta in questo punto di interruzione.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Ottiene le informazioni di richiesta di punto di interruzione che descrivono la richiesta di punto di interruzione.|  
  
## <a name="remarks"></a>Note  
 Dopo il programma in fase di debug sono stati caricati, una chiamata a [associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) associa un punto di interruzione in sospeso per il percorso di richiesto del programma.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)