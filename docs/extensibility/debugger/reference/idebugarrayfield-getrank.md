---
title: IDebugArrayField::GetRank | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetRank
helpviewer_keywords: IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 786f765e684f720c8c29b91331259e772bd5a007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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