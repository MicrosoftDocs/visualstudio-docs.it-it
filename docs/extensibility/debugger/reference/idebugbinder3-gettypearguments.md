---
title: IDebugBinder3::GetTypeArguments | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f5e06b51cfea731d94cd0eb53d91b4dbdf6b471
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Questo metodo recupera un elenco di tipi di argomenti associato all'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `skip`  
 [in] Numero di campi da ignorare prima di ottenere i tipi di argomento.  
  
 `count`  
 [in] Il numero di campi di argomento da restituire (specifica anche la dimensione del `ppFields` matrice).  
  
 `ppFields`  
 [in, out] Matrice di campi che verranno completati se la restituzione di questo metodo.  
  
 `pFetched`  
 [out] \(facoltativo) Numero di argomento tipo campi effettivamente restituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il numero di tipi di argomento può essere ottenuto in precedenza con [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)