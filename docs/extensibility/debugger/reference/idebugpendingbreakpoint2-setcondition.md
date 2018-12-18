---
title: IDebugPendingBreakpoint2::SetCondition | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2bc50ad1d763f196944e6246f891c5b4ed3893da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Imposta o modifica la condizione associata con il punto di interruzione in sospeso.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bpCondition`  
 [in] Oggetto [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struttura che specifica la condizione da impostare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Qualsiasi condizione che era precedentemente associato il punto di interruzione in sospeso verrà persi. Tutti i punti di interruzione associati da questo punto di interruzione viene chiamati per impostare le relative condizioni sul valore specificato nel `bpCondition` parametro.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)