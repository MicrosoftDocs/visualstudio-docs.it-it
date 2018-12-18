---
title: IDebugStackFrame2::GetCodeContext | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetCodeContext
helpviewer_keywords:
- IDebugStackFrame2::GetCodeContext
ms.assetid: 93d66159-a41d-49ef-982f-91bb4d073b74
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f5e5d41489b83283723717a262030bb96ca900a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getcodecontext"></a>IDebugStackFrame2::GetCodeContext
Ottiene il contesto del codice per questo stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCodeContext (   
   IDebugCodeContext2** ppCodeCxt  
);  
```  
  
```csharp  
int GetCodeContext (   
   out IDebugCodeContext2 ppCodeCxt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppCodeCxt`  
 [out] Restituisce un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che rappresenta il puntatore all'istruzione corrente in questo stack frame.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)