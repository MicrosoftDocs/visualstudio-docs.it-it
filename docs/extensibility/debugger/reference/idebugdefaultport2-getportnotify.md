---
title: IDebugDefaultPort2::GetPortNotify | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eca2893f388c4dabb244d042d652d3ab604d88bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Questo metodo ottiene un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaccia per la porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppPortNotify`  
 [out] Un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In genere, il `QueryInterface` metodo viene chiamato sull'oggetto che implementa il [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia per ottenere un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaccia. Tuttavia, esistono casi in cui viene implementata l'interfaccia desiderato su un oggetto diverso. Questo metodo nasconde le circostanze e restituisce il `IDebugPortNotify2` interfaccia dall'oggetto più appropriato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)