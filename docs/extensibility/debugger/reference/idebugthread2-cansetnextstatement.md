---
title: IDebugThread2::CanSetNextStatement | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0482f460e86944d80f7ae1988fa97118071466c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Determina se il puntatore all'istruzione corrente può essere impostato sul frame dello stack specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CanSetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int CanSetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pStackFrame`  
 Riservato per utilizzi futuri; impostare un valore null. Se si tratta di un valore null, utilizzare lo stack frame corrente.  
  
 `pCodeContext`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che descrive il percorso di codice da eseguire e il relativo contesto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se questo metodo restituisce `S_OK`, quindi chiamare il [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) per impostare effettivamente l'istruzione successiva.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)