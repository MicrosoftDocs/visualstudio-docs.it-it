---
title: IDebugPointerObject3::GetPointerAddress | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetPointerAddress
- IDebugPointerObject3::GetPointerAddress
ms.assetid: 4cc5af04-9e70-420d-8230-ef3108df6d51
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d21d797ca1370edee6eb1e664f3eb3ece35093fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpointerobject3getpointeraddress"></a>IDebugPointerObject3::GetPointerAddress
Recupera l'indirizzo del puntatore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPointerAddress (  
   UINT64* puAddress  
);  
```  
  
```csharp  
int GetPointerAddress (  
   out ulong puAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `puAddress`  
 [out] Restituisce l'indirizzo del puntatore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)