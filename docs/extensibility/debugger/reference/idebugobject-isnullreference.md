---
title: IDebugObject::IsNullReference | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a886bf56cfafc615099aa489f9d329229ea8727
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Verifica se l'oggetto è un riferimento null.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pfIsNull`  
 [out] Restituisce diverso da zero (`TRUE`) se l'oggetto è un riferimento null; in caso contrario, restituisce zero (`FALSE`).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un riferimento null significa che un oggetto vuoto o un oggetto che non è stato assegnato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)