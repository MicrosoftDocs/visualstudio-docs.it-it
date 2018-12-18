---
title: IDebugProcess3::Continue | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38bb11237d5016e3747c5a615e61144511c17fad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continua l'esecuzione di questo processo da uno stato di arresto. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene mantenuto, e il processo inizia a eseguire di nuovo.  
  
> [!NOTE]
>  Questo metodo deve essere utilizzato al posto di [continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread possa proseguire.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato su questo processo, indipendentemente dal numero di processi in fase di debug o il processo che ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio un passaggio) e continuare l'esecuzione come se non fosse mai arrestata prima del completamento dell'esecuzione precedente. Vale a dire, se un thread in questo processo stava eseguendo un'operazione del passaggio ed è stato arrestato perché è stato arrestato un altro processo e quindi `Continue` è stato chiamato, il thread deve essere completata l'operazione di passaggio su originale.  
  
 **Avviso** non invia un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)