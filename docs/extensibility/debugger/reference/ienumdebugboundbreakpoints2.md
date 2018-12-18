---
title: IEnumDebugBoundBreakpoints2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5faeb96f32170fefa1f93a69ca08228ceaec11f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Questa interfaccia enumera i punti di interruzione associati associate a un punto di interruzione in sospeso o punto di interruzione associato l'evento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia come parte del supporto per i punti di interruzione. Questa interfaccia deve essere implementata se sono supportati i punti di interruzione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Visual Studio chiama:  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione che sono stati generati.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione che sono stati associati.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione associato a tale punto di interruzione in sospeso.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugBoundBreakpoints2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Recupera un numero di punti di interruzione associati in una sequenza di enumerazione specificato.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Ignora un numero di punti di interruzione associati in una sequenza di enumerazione specificato.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione come enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Ottiene il numero di punti di interruzione associati in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Visual Studio utilizza i punti di interruzione associati rappresentati da questa interfaccia per aggiornare la visualizzazione dei punti di interruzione nell'IDE.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)