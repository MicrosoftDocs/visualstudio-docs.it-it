---
title: Collegamento e scollegamento di un programma | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a5b0783cd011c91b9592479c7b64c6cb6a1afaa1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-and-detaching-to-a-program"></a>Collegamento e scollegamento di un programma
Per collegare il debugger richiede l'invio la corretta sequenza di metodi ed eventi con gli attributi appropriati.  
  
## <a name="sequence-of-methods-and-events"></a>Sequenza di metodi ed eventi  
  
1.  Gestore di sessione di debug (SDM) chiama il [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo.  
  
     Basata sul modello di processo di debug del motore (DE), il `IDebugProgramNodeAttach2::OnAttach` restituisce uno dei metodi seguenti, che determina le operazioni successive.  
  
     Se `S_FALSE` viene restituito, il motore di debug è stato collegato correttamente al programma. In caso contrario, il [collegamento](../../extensibility/debugger/reference/idebugengine2-attach.md) metodo viene chiamato per completare il processo di collegamento.  
  
     Se `S_OK` viene restituito, viene caricata nello stesso processo come il SDM la Germania. Il SDM esegue le attività seguenti:  
  
    1.  Chiamate [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni di gestione della DE.  
  
    2.  Crea condivisione la Germania.  
  
    3.  Chiamate [allegare](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  Invia il DE un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) per il SDM con un `EVENT_SYNC` attributo.  
  
3.  Invia il DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) per il SDM con un `EVENT_SYNC` attributo.  
  
4.  Invia il DE un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) per il SDM con un `EVENT_SYNC_STOP` attributo.  
  
 La disconnessione da un programma è un semplice processo in due fasi, come indicato di seguito:  
  
1.  Le chiamate SDM [scollegamento](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  Invia il DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)