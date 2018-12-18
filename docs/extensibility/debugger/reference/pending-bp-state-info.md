---
title: PENDING_BP_STATE_INFO | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a4bf5f77ae24d83a0c0874d2cd03d1f5abbc0e2f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
Contiene informazioni sullo stato di un punto di interruzione che è possibile associare a un percorso di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```csharp  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## <a name="members"></a>Membri  
 stato  
 Un valore di [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) enumerazione che specifica lo stato del punto di interruzione in sospeso.  
  
 flag  
 Una combinazione di flag dal [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) enumerazione che specifica se il punto di interruzione è virtualizzato.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per il [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) (metodo) in cui viene compilato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)