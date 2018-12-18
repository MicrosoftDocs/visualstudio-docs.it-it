---
title: IDebugExpression2::EvaluateAsync | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13364d94f33eca33bf71b7077c19b9da54298ed7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Questo metodo valuta l'espressione in modo asincrono.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFlags`  
 [in] Una combinazione di flag dal [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumerazione che controllano la valutazione dell'espressione.  
  
 `pExprCallback`  
 [in] Questo parametro è sempre un valore null.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. È un codice di errore standard:  
  
|Error|Descrizione|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Attualmente viene valutata un'altra espressione e la valutazione dell'espressione simultanee non è supportata.|  
  
## <a name="remarks"></a>Note  
 Questo metodo deve restituire immediatamente dopo l'avvio la valutazione dell'espressione. Quando l'espressione viene valutata correttamente, un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) devono essere inviati al [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback di evento specificato tramite [Connetti ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) o [allegare](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per una semplice `CExpression` oggetto che implementa il [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaccia.  
  
```cpp  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)