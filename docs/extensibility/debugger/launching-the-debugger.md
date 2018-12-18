---
title: Avvio del Debugger | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7b5b596f553c0f84c9306bba010d2b97a33e1a16
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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