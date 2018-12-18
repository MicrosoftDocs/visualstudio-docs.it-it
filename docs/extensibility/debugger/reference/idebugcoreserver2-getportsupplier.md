---
title: IDebugCoreServer2::GetPortSupplier | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetPortSupplier
helpviewer_keywords:
- IDebugCoreServer2::GetPortSupplier
ms.assetid: acf181d4-ef42-4aa5-86f9-95fd5467ea31
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc8581c5ebeac88d89ae0541e3c0793554020107
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver2getportsupplier"></a>IDebugCoreServer2::GetPortSupplier
Recupera un fornitore di porta specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortSupplier(   
   REFGUID               guidPortSupplier,  
   IDebugPortSupplier2** ppPortSupplier  
);  
```  
  
```csharp  
int GetPortSupplier(   
   ref Guid                guidPortSupplier,  
   out IDebugPortSupplier2 ppPortSupplier  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidPortSupplier`  
 [in] GUID del fornitore porta da recuperare.  
  
 `ppPortSupplier`  
 [out] Restituisce un [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) oggetto che rappresenta il fornitore della porta desiderata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)