---
title: IDebugProgramNodeAttach2::OnAttach | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords: IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a6b0f74ef5b14fb9e8971c0d539cc2e875658341
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Collega al programma associato o rinvia il collegamento del processo di [collegamento](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidProgramId`  
 [in] `GUID` da assegnare al programma associato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se il [collegamento](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo non deve essere chiamato. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato durante il processo di collegamento, prima di [collegamento](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo viene chiamato. Il `OnAttach` metodo può eseguire il processo di collegamento (in questo caso, questo metodo restituisce `S_FALSE`) o rinviare il processo di collegamento per il `IDebugEngine2::Attach` metodo (il `OnAttach` restituisce `S_OK`). In entrambi i casi il `OnAttach` metodo può impostare il `GUID` del programma in fase di debug per il dato `GUID`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)