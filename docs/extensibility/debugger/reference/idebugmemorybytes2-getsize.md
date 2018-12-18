---
title: IDebugMemoryBytes2::GetSize | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fce2d9beecb6c2a51d64e229dcf386795ab55f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
Recupera la dimensione, in byte, della memoria rappresentato da questo [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSize(   
   UINT64* pqwSize  
);  
```  
  
```csharp  
int GetSize(  
   out ulong pqwSize  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pqwSize`  
 [out] Restituisce le dimensioni, in byte dello spazio di memoria.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)