---
title: IDebugReference2::GetMemoryContext | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetMemoryContext
helpviewer_keywords:
- IDebugReference2::GetMemoryContext
ms.assetid: 47fc3827-07a0-4eee-b7f4-fc1c62e6b25c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87d6137e3cc229fe16111e7c9078cdee1f427ea8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugreference2getmemorycontext"></a>IDebugReference2::GetMemoryContext
Ottiene il contesto di memoria di un riferimento. Riservato per utilizzi futuri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMemoryContext (   
   IDebugMemoryContext2** ppMemory  
);  
```  
  
```csharp  
int GetMemoryContext (   
   out IDebugMemoryContext2 ppMemory  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppMemory`  
 [out] Restituisce il [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetto che rappresenta la memoria associata al valore del riferimento.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)