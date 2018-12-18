---
title: IDebugProgramNameChangedEvent2 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13ce56d169c76bb88c19866e50fd707cdd8cb450
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Inviato dal motore di debug (DE) al gestore di sessione di debug (SDM) quando viene modificato il nome di un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per i report che è stato modificato il nome del programma. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Usa il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di **IDebugEvent2** interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento per segnalare una modifica del nome del programma. La Germania, questo evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando è collegato al programma sottoposto a debug. Il fornitore di porta personalizzato invia questo evento tramite che l'interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll