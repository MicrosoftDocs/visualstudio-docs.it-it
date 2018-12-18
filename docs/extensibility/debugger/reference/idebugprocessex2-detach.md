---
title: IDebugProcessEx2::Detach | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0423ae28bfee6e9acf10e2a9682e58a973c37d70
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Questo metodo indica il processo che una sessione non è più il debug del processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pSession`  
 [in] Un valore che identifica in modo univoco la sessione per il processo da scollegare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'interfaccia passato `pSession` è venga considerato solo un cookie, un valore che identifica in modo univoco il gestore di sessione di debug che originariamente connesso a questo processo, nessuno dei metodi dell'interfaccia fornite sono funzionali.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)