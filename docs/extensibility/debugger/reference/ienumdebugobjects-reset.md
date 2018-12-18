---
title: IEnumDebugObjects::Reset | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28cf4f5936ee90a225d05f5b3fe959c21fca3617
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Questo metodo reimposta l'enumerazione al primo elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Dopo che questo metodo viene chiamato, la chiamata successiva a [Avanti](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) restituisce il primo elemento dell'enumerazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [avanti](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)