---
title: IDebugProcess3::Execute | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 349f792826bcfaa6ec3af1e10069e9c7182868bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Continua l'esecuzione di questo processo da uno stato di arresto. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene cancellato e il processo inizia a eseguire di nuovo.  
  
> [!NOTE]
>  Questo metodo deve essere utilizzato al posto di [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta l'esecuzione del thread.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 Quando l'utente avvia l'esecuzione da uno stato di interruzione di thread di altri processi, questo metodo viene chiamato su questo processo. Questo metodo viene chiamato anche quando l'utente seleziona il **avviare** comando il **Debug** menu nell'IDE. L'implementazione di questo metodo può essere semplice come chiamare il [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metodo sul thread corrente del processo.  
  
> [!WARNING]
>  Non inviare un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario il debugger potrebbe bloccarsi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)