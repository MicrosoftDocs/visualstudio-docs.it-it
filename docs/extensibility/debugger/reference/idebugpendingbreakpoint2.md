---
title: IDebugPendingBreakpoint2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPendingBreakpoint2
helpviewer_keywords: IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ef986bd657a080c08fd0ebb85908ba59757bf207
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Questa interfaccia rappresenta un punto di interruzione che è possibile associare a un percorso di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia come parte del supporto per i punti di interruzione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crea un punto di interruzione in sospeso da un [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfaccia. Una chiamata a [associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea un `IDebugBreakpoint2` interfaccia che rappresenta un punto di interruzione associato nel programma.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugPendingBreakpoint2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se è possibile associare il punto di interruzione in sospeso in un percorso di codice.|  
|[Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa il punto di interruzione in sospeso a uno o più percorsi di codice.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ottiene lo stato di questo punto di interruzione.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta di punto di interruzione che è stata utilizzata per creare il punto di interruzione in sospeso.|  
|[Virtualizzare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Alterna lo stato virtualizzato di questo punto di interruzione.|  
|[Abilitare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Attiva o disattiva lo stato di abilitazione di questo punto di interruzione.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Imposta o modifica la condizione associata a questo punto di interruzione.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Imposta o modifica il numero di sessione associato a questo punto di interruzione.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera tutti i punti di interruzione associati da questo punto di interruzione in sospeso.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera tutti i punti di interruzione di errore che ha generato da questo punto di interruzione in sospeso.|  
|[Eliminazione](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina il punto di interruzione in sospeso e tutti i punti di interruzione associati da esso.|  
  
## <a name="remarks"></a>Note  
 `IDebugPendingBreakpoint2`può essere considerato come un provider di tutte le necessarie informazioni necessarie per associare un punto di interruzione al codice che può essere applicato a uno o più programmi.  
  
 Un punto di interruzione in sospeso può produrre più di un punto di interruzione associato. Ad esempio, un punto di interruzione in un modello di stile di C++ in grado di generare un punto di interruzione associato per ogni istanza univoca di tale modello.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)