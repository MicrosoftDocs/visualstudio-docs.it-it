---
title: IDebugProgramPublisher2::SetDebuggerPresent | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5725d6e143f10cd3a3fae18398ec0cb08729fa34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
Indica il server di pubblicazione del programma che un debugger è presente e in esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetDebuggerPresent(  
   BOOL fDebuggerPresent  
);  
```  
  
```csharp  
int SetDebuggerPresent(  
   int fDebuggerPresent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fDebuggerPresent`  
 [in] Diverso da zero (`TRUE`) se è presente un debugger, zero (`FALSE`) in caso contrario.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 La presenza o assenza di un debugger viene riflessa nei dati restituiti dal [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metodo: il valore restituito sono è impostato o cancellato da una precedente chiamata al `SetDebuggerPresent` metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)