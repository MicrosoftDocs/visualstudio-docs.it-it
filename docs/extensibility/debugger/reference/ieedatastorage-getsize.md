---
title: IEEDataStorage::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64f78005e4f3f7027cb6621e67cfbe44be4af3a0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848746"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Restituisce il numero di byte contenuti in questo oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSize(  
   ULONG* size  
);  
```  
  
```csharp  
int GetSize(  
   out uint size  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `size`  
 [out] Il numero di byte contenuti in questo oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Usare la [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) metodo per recuperare i byte di dati effettivi.  
  
## <a name="see-also"></a>Vedere anche  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)