---
title: Chiusura e disconnessione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5af218098f6d79cf6208c66b314c35d2471af15
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="termination-and-detaching"></a>Chiusura e disconnessione
Di seguito vengono illustrate la terminazione normale.  
  
## <a name="discussion"></a>Discussione  
 Dopo il [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfaccia continua, se non esistono punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione da sottoporre a debug, il programma in fase di debug verrà eseguito fino al completamento. Si tratta di chiusura normale.  
  
 È necessario inviare un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) per implementare una chiusura normale. Questa operazione richiede l'implementazione di [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)