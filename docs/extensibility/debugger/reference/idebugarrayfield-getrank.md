---
title: IDebugArrayField::GetRank | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4fee642bb5f19efb62b631d71d3ba95eec45c0be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Ottiene il numero di dimensioni o il numero di dimensioni della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwRank`  
 [out] Restituisce il rango.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il numero di dimensioni della matrice corrisponde al numero di dimensioni. In C++ e c#, le matrici multidimensionali sono realmente le matrici di matrici e pertanto possono essere considerate solo una matrice unidimensionale (e `GetRank` metodo restituisce sempre 1). In [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], d'altra parte, le matrici multidimensionali sono gestite in modo diverso e il numero di dimensioni di tale matrice riflette il numero di dimensioni (e `GetRank` metodo restituisce sempre il numero di dimensioni).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)