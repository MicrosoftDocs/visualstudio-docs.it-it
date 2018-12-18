---
title: IDebugProgramHost2::GetHostName | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 139c7c991235f57dba670c15721751dca71c550f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Ottiene il titolo, un nome descrittivo o un nome di file del processo di hosting di questo programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwType`  
 [in] Un valore di [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumerazione.  
  
 `pbstrHostName`  
 [out] Restituisce il nome richiesto del processo di hosting.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In un'implementazione tipica di questo metodo, il `dwType` parametro viene ignorato e viene restituito un nome descrittivo del computer host. Un'altra implementazione possibili consiste nel passare il `dwType` parametro a una chiamata al [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) metodo per ottenere il nome.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)