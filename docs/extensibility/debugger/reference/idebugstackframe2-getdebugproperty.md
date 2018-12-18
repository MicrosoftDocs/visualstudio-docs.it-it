---
title: IDebugStackFrame2::GetDebugProperty | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d0fcb648f25667d47a164c14443bafd14cc315f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
Ottiene una descrizione delle proprietà di uno stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppDebugProp  
);  
```  
  
```csharp  
int GetDebugProperty (   
   out IDebugProperty2 ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppDebugProp`  
 [out] Restituisce un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto che descrive le proprietà dello stack frame corrente.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 La chiamata di [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metodo con filtri appropriati può recuperare le variabili locali, i parametri del metodo, i registri e puntatore "this" associato al frame dello stack.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)