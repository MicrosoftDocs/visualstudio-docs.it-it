---
title: IDebugEventCallback2::Event | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEventCallback2::Event
helpviewer_keywords: IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0a7e5d4d20ae7e4409599a77250986b759f152fb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Invia una notifica di eventi di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pEngine`  
 [in] Un [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) oggetto che rappresenta il motore di debug (DE) che invia l'evento. Per compilare questo parametro è necessario un Germania.  
  
 `pProcess`  
 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) oggetto che rappresenta il processo in cui si verifica l'evento. Questo parametro viene inserito dal gestore di sessione di debug (SDM). Un Germania passa sempre un valore null per questo parametro.  
  
 `pProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma in cui si verifica questo evento. Per la maggior parte degli eventi, questo parametro non è un valore null.  
  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread in cui si verifica questo evento. Per eventi di arresto, questo parametro non può essere un valore null come frame dello stack viene ottenuto da questo parametro.  
  
 `pEvent`  
 [in] Un [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) oggetto che rappresenta l'evento di debug.  
  
 `riidEvent`  
 [in] GUID che identifica l'interfaccia eventi di ottenere il `pEvent` parametro.  
  
 `dwAttrib`  
 [in] Una combinazione di flag dal [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Quando si chiama questo metodo, il `dwAttrib` parametro deve corrispondere al valore restituito dal [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) metodo chiamato per l'oggetto evento passato il `pEvent` parametro.  
  
 Tutti gli eventi di debug vengono registrati in modo asincrono, indipendentemente dal fatto che un evento stesso sia asincrono o meno. Quando questo metodo viene chiamato un Germania, il valore restituito indica se l'evento è stato elaborato, solo se è stato ricevuto l'evento. In realtà, in molti casi, l'evento non è stato elaborato quando questo metodo viene restituito.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)