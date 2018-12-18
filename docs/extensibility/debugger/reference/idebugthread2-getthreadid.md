---
title: IDebugThread2::GetThreadId | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac1701b3f52975e962860d558bc70b1847eef8e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Ottiene l'identificatore del thread di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetThreadId (   
   DWORD* pdwThreadId  
);  
```  
  
```csharp  
int GetThreadId (   
   out uint pdwThreadId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwThreadId`  
 [out] Restituisce l'identificatore del thread di sistema.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un ID thread viene utilizzato per identificare un thread tra tutti gli altri thread in un processo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per una semplice `CProgram` oggetto che implementa il [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) interfaccia.  
  
```cpp  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)