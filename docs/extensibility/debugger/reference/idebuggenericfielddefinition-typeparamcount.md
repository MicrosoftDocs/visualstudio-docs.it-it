---
title: IDebugGenericFieldDefinition::TypeParamCount | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11e8dcebf06c5779ee51b11e315c5277d99b4971
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebuggenericfielddefinitiontypeparamcount"></a>IDebugGenericFieldDefinition::TypeParamCount
Recupera il numero di parametri di tipo associato al campo generico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT TypeParamCount(  
   ULONG32* pcParams  
);  
```  
  
```csharp  
int TypeParamCount(  
   ref uint pcParams  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcParams`  
 [in, out] Numero di parametri di tipo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se elenco\<T >, questo metodo restituisce 1 e, se elenco\<T1, T2 >, questo metodo restituisce 2. Questo metodo restituisce 0 se non sono presenti parametri di tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)