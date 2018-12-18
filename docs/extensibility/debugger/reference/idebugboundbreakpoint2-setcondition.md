---
title: IDebugBoundBreakpoint2::SetCondition | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 94b131820fdd6bd2b83a9e54fd450cbb19c8064a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Imposta o modifica la condizione associata a questo punto di interruzione associato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bpCondition`  
 [in] Un valore di [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) enumerazione che descrive la condizione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_BP_DELETED` se lo stato dell'oggetto punto di interruzione associato è impostato su `BPS_DELETED` (in parte il [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumerazione).  
  
## <a name="remarks"></a>Note  
 Qualsiasi condizione che era precedentemente associato a questo punto di interruzione viene persa.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)