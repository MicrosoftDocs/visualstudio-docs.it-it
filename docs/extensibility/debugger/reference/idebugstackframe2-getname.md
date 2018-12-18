---
title: IDebugStackFrame2::GetName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetName
helpviewer_keywords:
- IDebugStackFrame2::GetName
ms.assetid: 069d4f96-363f-404e-9c89-5318c4c9821b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4b4e5a6ac925762e23766938141dfcddb3fe598
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getname"></a>IDebugStackFrame2::GetName
Ottiene il nome del frame dello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrName`  
 [out] Restituisce il nome del frame dello stack.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il nome di uno stack frame è in genere il nome del metodo in esecuzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)