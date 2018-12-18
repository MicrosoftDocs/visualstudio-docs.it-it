---
title: IDebugStackFrame3::InterceptCurrentException | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords: IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9842527f90d9b2df7308f1e80e337de2848d9179
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Chiamato dal debugger sullo stack frame corrente quando desidera intercettare l'eccezione corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFlags`  
 [in] Specifica le azioni diverse. Attualmente, solo il [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) valore `IEA_INTERCEPT` è supportato e deve essere specificato.  
  
 `pqwCookie`  
 [out] Valore univoco che identifica una particolare eccezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
 Di seguito sono la restituzione di errori più comuni.  
  
|Error|Descrizione|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Non è possibile intercettare l'eccezione corrente.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Il frame di esecuzione corrente non è stata ancora ricerca per un gestore.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Questo metodo non è supportato per questo fotogramma.|  
  
## <a name="remarks"></a>Note  
 Quando viene generata un'eccezione, il debugger ottiene il controllo dalla fase di esecuzione nei punti chiave durante il processo di gestione delle eccezioni. Durante queste istante chiave, il debugger può richiedere lo stack frame corrente se il frame desidera intercettare l'eccezione. In questo modo, un'eccezione intercettata è essenzialmente un gestore di eccezioni in tempo reale per uno stack frame, anche se tale stack frame non dispone di un gestore di eccezioni (ad esempio, un blocco try/catch nel codice programma).  
  
 Quando il debugger desidera sapere se è necessario intercettare l'eccezione, viene chiamato questo metodo sull'oggetto stack frame corrente. Questo metodo è responsabile della gestione di tutti i dettagli dell'eccezione. Se il [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) interfaccia non è implementata o `InterceptStackException` il metodo restituisce un errore, quindi il debugger continua l'elaborazione in genere l'eccezione.  
  
> [!NOTE]
>  Le eccezioni possono essere intercettate solo nel codice gestito, vale a dire quando il programma in fase di debug viene eseguita nel runtime di .NET. Naturalmente, è possibile implementare gli implementatori del linguaggio di terze parti `InterceptStackException` nei propri motori di debug, se richiesto.  
  
 Una volta completata, l'intercettazione un [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) viene segnalato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)