---
title: IEnumDebugAddresses::Clone | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugAddresses::Clone
helpviewer_keywords:
- IEnumDebugAddresses::Clone method
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b6b5ddb4eabcbc3d15650e91ee7cecd7fdbb648
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugaddressesclone"></a>IEnumDebugAddresses::Clone
Questo metodo restituisce una copia dell'enumerazione corrente come oggetto separato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Clone(  
   IEnumDebugAddresses** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugAddresses ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce una copia di questa enumerazione come oggetto separato.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 La copia dell'enumerazione ha lo stesso stato originale al momento che questo metodo viene chiamato. Tuttavia, stati la copia e l'originale sono separati e possono essere modificati singolarmente.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)