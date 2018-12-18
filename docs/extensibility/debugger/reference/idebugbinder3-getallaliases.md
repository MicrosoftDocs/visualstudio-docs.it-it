---
title: IDebugBinder3::GetAllAliases | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6da1b26b41c80d0417da16f478ef3f6672edd12a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Questo metodo recupera un elenco di alias dal programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `uRequest`  
 [in] Il numero massimo di alias da restituire (specifica la lunghezza della matrice passata in `ppAliases`).  
  
 `ppAliases`  
 [in, out] Matrice da riempire con alias (se si tratta di un valore null e `uRequest` è 0, verrà restituito il conteggio di alias che può essere restituito da `puFetched`).  
  
 `puFetched`  
 [out] Restituisce il numero di alias ottenuto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)