---
title: IDebugEntryPointEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fa36778960818fa6e4bfbd94f1718a01b2b6294
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Il motore di debug (DE) invia questa interfaccia al gestore di sessione di debug (SDM) quando il programma sta per eseguire la prima istruzione del codice utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia come parte delle normale operazioni. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Usa il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento quando il programma in fase di debug è stato caricato ed è pronto per l'esecuzione della prima istruzione del codice utente. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando è collegato al programma sottoposto a debug.  
  
## <a name="remarks"></a>Note  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) viene inviato quando il programma sta per eseguire l'istruzione prima. Ad esempio, `IDebugEntryPoint2` viene inviato quando il programma sta per eseguire l'utente `main` (funzione).  
  
 Quando la Germania Invia `IDebugEntryPointEvent2`, la posizione corrente del codice deve essere la prima istruzione del codice utente, ad esempio `main`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)