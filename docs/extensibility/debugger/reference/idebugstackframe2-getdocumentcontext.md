---
title: IDebugStackFrame2::GetDocumentContext | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetDocumentContext
helpviewer_keywords:
- IDebugStackFrame2::GetDocumentContext
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14e7374fbea697b86d9ee838a6b8a76a57f920ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getdocumentcontext"></a>IDebugStackFrame2::GetDocumentContext
Ottiene il contesto di documento per lo stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppCxt  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppCxt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppCxt`  
 [out] Restituisce un [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) oggetto che rappresenta la posizione corrente nel documento di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo è più veloce rispetto a chiamare il [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) metodo e chiamando quindi il [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) metodo nel contesto del codice. Tuttavia, non è garantito che questo metodo viene implementato da ogni motore di debug (DE).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)