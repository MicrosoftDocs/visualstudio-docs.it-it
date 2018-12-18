---
title: IDebugPendingBreakpoint2::SetPassCount | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21e39c54249add3b5d57cd6db907256122aab56b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Imposta o modifica il numero di sessione associato al punto di interruzione in sospeso.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bpPassCount`  
 [in] Oggetto [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) struttura che contiene il numero di passaggio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_BP_DELETED` se il punto di interruzione è stato eliminato.  
  
## <a name="remarks"></a>Note  
 Qualsiasi numero di passaggio era precedentemente associato il punto di interruzione in sospeso verrà perso. Tutti i punti di interruzione associati da questo punto di interruzione viene chiamati per impostare il conteggio di passaggio la `bpPassCount` parametro.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)