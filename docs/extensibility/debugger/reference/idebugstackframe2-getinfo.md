---
title: IDebugStackFrame2::GetInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b291af7f8f50d672655a098e22ef938d99e0daed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Ottiene una descrizione del frame dello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetInfo (   
   FRAMEINFO_FLAGS dwFieldSpec,  
   UINT            nRadix,  
   FRAMEINFO*      pFrameInfo  
);  
```  
  
```csharp  
int GetInfo (   
   enum_FRAMEINFO_FLAGS dwFieldSpec,  
   uint                 nRadix,  
   FRAMEINFO[]          pFrameInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFieldSpec`  
 [in] Una combinazione di flag dal [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumerazione che specifica quali campi del `pFrameInfo` parametro devono essere compilati.  
  
 `nRadix`  
 [in] La radice da utilizzare per la formattazione di eventuali informazioni numeriche.  
  
 `pFrameInfo`  
 [out] Oggetto [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struttura che viene compilato con la descrizione del frame dello stack.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)