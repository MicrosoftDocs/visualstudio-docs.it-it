---
title: IDebugExceptionEvent2::PassToDebuggee | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8e6b53a07f191d967bbd676e6fcfc96b53dc14
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Specifica se l'eccezione deve essere passata per il programma in fase di debug quando si riprende l'esecuzione, o se l'eccezione deve essere ignorato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fPass`  
 [in] Diverso da zero (`TRUE`) se l'eccezione deve essere passato programma sottoposto a debug durante l'esecuzione riprende oppure zero (`FALSE`) se l'eccezione deve essere ignorato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Chiamare questo metodo non determina effettivamente il codice da eseguire nel programma sottoposto a debug. La chiamata è semplicemente per impostare lo stato per l'esecuzione di codice successiva. Ad esempio, le chiamate ai [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) metodo può restituire `S_OK` con il [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` campo impostato su `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 L'IDE è possibile che venga visualizzato il [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) eventi e chiamate di [continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md) metodo. Il motore di debug (DE) deve avere un comportamento predefinito di gestire il caso di `PassToDebuggee` non viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)