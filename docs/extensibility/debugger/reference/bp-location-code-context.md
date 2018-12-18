---
title: BP_LOCATION_CODE_CONTEXT | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_CONTEXT
helpviewer_keywords:
- BP_LOCATION_CODE_CONTEXT structure
ms.assetid: 37412896-021a-4f73-9bb7-4125502c2e18
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03ae1050b0324fcf2732bbeb0eb9d091878bef0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bplocationcodecontext"></a>BP_LOCATION_CODE_CONTEXT
Descrive il percorso di un punto di interruzione associato direttamente a un indirizzo nel programma sottoposto a debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _BP_LOCATION_CODE_CONTEXT {   
   IDebugCodeContext2* pCodeContext;  
} BP_LOCATION_CODE_CONTEXT;  
```  
  
## <a name="members"></a>Membri  
 pCodeContext  
 Il [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che identifica la posizione del punto di interruzione nel codice.  
  
## <a name="remarks"></a>Note  
 Questa struttura è membro il [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struttura come parte di un'unione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)