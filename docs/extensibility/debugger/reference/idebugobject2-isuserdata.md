---
title: IDebugObject2::IsUserData | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c20b4e531284156b8790b1ca65b32c85d1db997
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Determina se l'oggetto rappresenta i dati utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pfUser`  
 [out] Restituisce zero (`TRUE`) se l'oggetto rappresenta i dati dell'utente; zero (`FALSE`) in caso contrario.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Dati utente sono qualsiasi oggetto che fa parte di un modulo designato come JustMyCode (opzione configurabile dall'utente che contrassegna un modulo come codice utente e pertanto visibili in una traccia dello stack).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)