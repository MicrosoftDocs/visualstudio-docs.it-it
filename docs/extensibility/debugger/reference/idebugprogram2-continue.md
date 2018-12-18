---
title: IDebugProgram2::Continue | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f52fccf640cca32d4291b3d6fb8626c38370ded3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continua l'esecuzione di questo programma da uno stato di arresto. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene mantenuto, e il programma viene avviato l'esecuzione di nuovo.  
  
> [!NOTE]
>  Questo metodo è deprecato. Utilizzare il [continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metodo invece.  
  
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
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato su questo programma, indipendentemente da quante applicazioni sono in fase di debug o il programma che ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio un passaggio) e continuare l'esecuzione come se non fosse mai arrestata prima del completamento dell'esecuzione precedente. Vale a dire, se un thread in questo programma stava eseguendo un'operazione del passaggio ed è stato arrestato perché un altro programma arrestato e quindi questo metodo è stato chiamato, il programma necessario completare l'operazione di passaggio su originale.  
  
> [!WARNING]
>  Non inviare un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario il debugger potrebbe bloccarsi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)