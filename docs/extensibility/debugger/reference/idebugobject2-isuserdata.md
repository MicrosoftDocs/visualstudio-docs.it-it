---
title: IDebugObject2::IsUserData | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::IsUserData
helpviewer_keywords: IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5cd56e2b83411710fa110c7abd65d965d828083d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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