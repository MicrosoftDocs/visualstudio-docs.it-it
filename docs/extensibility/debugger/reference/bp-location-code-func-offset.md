---
title: BP_LOCATION_CODE_FUNC_OFFSET | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d312824bb88022cba9b58945cb5f3e78c13b837
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bplocationcodefuncoffset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Descrive la posizione di offset di un punto di interruzione in una funzione nel codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {   
   BSTR                     bstrContext;  
   IDebugFunctionPosition2* pFuncPos;  
} BP_LOCATION_CODE_FUNC_OFFSET;  
```  
  
## <a name="members"></a>Membri  
 `bstrContext`  
 Il contesto del punto di interruzione, in genere un nome di metodo o una funzione come illustrato in uno stack di chiamate.  
  
 `pFuncPos`  
 Il [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) oggetto che descrive il nome della funzione e la posizione relativa a partire dall'inizio della funzione.  
  
## <a name="remarks"></a>Note  
 Questa struttura è membro il [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struttura come parte di un'unione.  
  
 Il `pFuncPos` membro indica la posizione in cui il punto di interruzione di funzione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)