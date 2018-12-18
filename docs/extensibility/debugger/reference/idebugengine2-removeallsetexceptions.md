---
title: IDebugEngine2::RemoveAllSetExceptions | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords: IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1412022d5eefffcaab74a33cb76f1580bc910c0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Rimuove l'elenco delle eccezioni, che l'IDE è impostato per un linguaggio o una particolare architettura di runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidType`  
 [in] GUID per la lingua o il GUID per il motore di debug specifico per un'architettura della fase di esecuzione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Sono state impostate le eccezioni rimosse da questo metodo dalle chiamate precedenti per il [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) metodo.  
  
 Per rimuovere un'eccezione specifica, chiamare il [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)