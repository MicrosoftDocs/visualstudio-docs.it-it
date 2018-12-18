---
title: IDebugBoundBreakpoint2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2
helpviewer_keywords: IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6ce63ce7f7d6a4f438c0e9f622c34a2231afd6ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Questa interfaccia rappresenta un punto di interruzione è associata a un percorso di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia come parte del supporto per i punti di interruzione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea questa interfaccia. Le chiamate a [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) e [Avanti](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) anche possibile ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugBoundBreakpoint2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in sospeso da cui è stato creato il punto di interruzione associato specificato.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ottiene lo stato del punto di interruzione associato.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Ottiene il numero di passaggi corrente per questo punto di interruzione associato.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione di punto di interruzione che descrive il punto di interruzione.|  
|[Abilitare](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Abilita o disabilita il punto di interruzione.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Imposta il numero di passaggi per questo punto di interruzione associato.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Imposta o modifica la condizione associata a questo punto di interruzione associato.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Imposta o modifica il numero di sessione associato a questo punto di interruzione associato.|  
|[Eliminazione](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina il punto di interruzione.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Avanti](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)