---
title: IDebugProcess3::Step | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cbc19c339e5d53bc9dde13ebd4a1bbddd214810c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Fa sì che il processo eseguire un'istruzione o istruzione.  
  
> [!NOTE]
>  Questo metodo deve essere utilizzato al posto di [passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```csharp  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread viene eseguito.  
  
 `sk`  
 [in] Uno del [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) valori.  
  
 `step`  
 [in] Uno del [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) valori.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 In caso di qualsiasi la sincronizzazione dei thread o comunicazione tra thread, altri thread nel processo deve essere eseguito quando un thread specifico è l'esecuzione di istruzioni.  
  
 **Avviso** non invia un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)