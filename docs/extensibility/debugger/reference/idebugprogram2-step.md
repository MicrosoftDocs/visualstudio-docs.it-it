---
title: IDebugProgram2::Step | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10685adb27c9bf2e962beccb7e68f19ce5c27eeb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Esegue un passaggio.  
  
> [!NOTE]
>  Questo metodo è deprecato. Utilizzare il [passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md) metodo invece.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread viene eseguito.  
  
 `sk`  
 [in] Un valore di [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) enumerazione che specifica il tipo di passaggio.  
  
 `step`  
 [in] Un valore di [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) enumerazione che specifica l'unità del passaggio (ad esempio, tramite l'istruzione o istruzione).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In caso di qualsiasi la sincronizzazione dei thread o comunicazione tra thread, altri thread nel programma deve essere eseguito quando un thread specifico è l'esecuzione di istruzioni.  
  
> [!WARNING]
>  Non inviare un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario il debugger potrebbe bloccarsi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)