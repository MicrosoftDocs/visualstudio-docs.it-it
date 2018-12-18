---
title: IDebugEngine3::SetJustMyCodeState | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fda672cc9d6861520b9da3a894b94d51f4100683
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Le informazioni di stato JustMyCode, questo metodo indica al motore di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fUpdate`  
 [in] Diverso da zero (`TRUE`) per aggiornare le informazioni correnti, zero (`FALSE`) per reimpostare tutte le informazioni (ignorando qualsiasi tipo impostato in precedenza).  
  
 `dwModules`  
 [in] Numero di strutture di informazioni in `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Matrice di [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) strutture da utilizzare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 JustMyCode è il concetto di debug solo il codice che appartiene a un utente e l'esclusione di tutto il codice intermedio, ad esempio di codice di sistema, anche se il codice sorgente è disponibile per il codice di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)