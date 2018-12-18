---
title: Avvio del Debugger | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2606e0f6c7d5dfe17e4c82528c36b3f7cdc26c5e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="launching-the-debugger"></a>Avvio del Debugger
Avvio del debugger richiede l'invio la corretta sequenza di metodi ed eventi con i relativi attributi appropriati.  
  
## <a name="sequences-of-methods-and-events"></a>Sequenze di metodi ed eventi  
  
1.  Gestore di sessione di debug (SDM) viene chiamato scegliendo il **Debug** menu e scegliendo **avviare**. Vedere [avviando un programma](../../extensibility/debugger/launching-a-program.md) per ulteriori informazioni.  
  
2.  Le chiamate SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo.  
  
3.  Basata sul modello di processo di debug del motore (DE), il `IDebugProgramNodeAttach2::OnAttach` restituisce uno dei metodi seguenti, che determina le operazioni successive.  
  
     Se `S_FALSE` viene restituito, il motore di debug (DE) da caricare in fase di macchina virtuale.  
  
     oppure  
  
     Se `S_OK` viene restituito, viene caricata la Germania in-process del messaggio SDM. Il SDM esegue quindi le attività seguenti:  
  
    1.  Chiamate [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni di gestione della DE.  
  
    2.  Crea condivisione la Germania.  
  
    3.  Chiamate [allegare](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Invia il DE un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) per il SDM con un `EVENT_SYNC` attributo.  
  
5.  Invia il DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) per il SDM con un `EVENT_SYNC` attributo.  
  
6.  Invia il DE un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) per il SDM con un `EVENT_SYNC` attributo.  
  
7.  Invia il DE un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) per il SDM con un `EVENT_SYNC` attributo.  
  
8.  Invia il DE un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) per il SDM con un `EVENT_SYNC` attributo.  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi del Debugger chiamata](../../extensibility/debugger/calling-debugger-events.md)   
 [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)