---
title: IDebugProgramEx2::Attach | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c58f576a0126472ad60ceeb5fc5289b668bd54dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Connettere una sessione a un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto che rappresenta la funzione di callback che il motore di debug collegato invia eventi.  
  
 `dwReason`  
 [in] Un valore di [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumerazione che descrive il motivo per l'operazione di collegamento.  
  
 `pSession`  
 [in] Un valore che identifica in modo univoco la sessione che si sta connettendo al programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Questo metodo deve restituire `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` se il programma è già collegato.  
  
## <a name="remarks"></a>Note  
 La porta che contiene il programma è possibile utilizzare il valore in `pSession` per determinare quale sessione sta tentando di connettersi al programma. Ad esempio, se una porta consente la sessione di debug solo uno di connettersi a un processo alla volta, la porta possibile determinare se la stessa sessione è già collegata ad altri programmi nel processo.  
  
> [!NOTE]
>  L'interfaccia passato `pSession` deve essere considerata solo come un cookie, un valore che identifica in modo univoco il gestore di sessione debug collegamento a questo programma, i metodi di interfaccia specificato non è funzionale.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)