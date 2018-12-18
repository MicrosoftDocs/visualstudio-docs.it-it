---
title: IDebugProcess2::EnumThreads | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 786a3b4b5988b66e1fccc624154eeef67285ec84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Recupera un elenco di tutti i thread in esecuzione nel processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) oggetto che contiene un elenco di tutti i thread in tutti i programmi del processo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo enumera i thread in esecuzione in ogni programma e quindi le combina in una vista dei thread del processo. Un singolo thread possono essere eseguite in più programmi. Questo metodo enumera solo una volta tale thread.  
  
 Questo metodo visualizza un elenco di thread del processo senza duplicati. In caso contrario, per enumerare i thread in esecuzione in un particolare programma, utilizzare il [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)