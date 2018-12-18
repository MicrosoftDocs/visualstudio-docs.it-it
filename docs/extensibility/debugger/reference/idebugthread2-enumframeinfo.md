---
title: IDebugThread2::EnumFrameInfo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4781533d533228e07b4268f5c92b662cf7cda122
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Recupera un elenco di stack frame per il thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFieldSpec`  
 [in] Una combinazione di flag dal [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumerazione che specifica quali campi del [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture devono essere compilati. Specificare il `FIF_FUNCNAME_FORMAT` flag per formattare il nome della funzione in un'unica stringa.  
  
 `nRadix`  
 [in] Radice utilizzata per la formattazione delle informazioni numeriche nell'enumeratore.  
  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) oggetto che contiene un elenco di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture che descrive lo stack frame.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Frame del thread sono enumerati in ordine, con il fotogramma corrente enumerata prima e il meno recente enumerato ultima.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)