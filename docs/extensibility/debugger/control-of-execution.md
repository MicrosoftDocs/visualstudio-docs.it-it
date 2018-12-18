---
title: Controllo dell'esecuzione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9fc47a0b73d07e4b24ef55c736ad80197f282cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="control-of-execution"></a>Controllo di esecuzione
Il motore di debug (DE) in genere uno dei seguenti eventi Invia come ultimo evento di avvio:  
  
-   L'evento punto di ingresso, se la connessione a un programma appena avviato  
  
-   L'evento complete di carico, se la connessione a un programma che è già in esecuzione  
  
 Entrambi questi eventi sono eventi di arresto, vale a dire che la Germania attende una risposta da parte dell'utente tramite l'IDE. Per ulteriori informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>L'evento di arresto  
 Quando viene inviato un evento di arresto per la sessione di debug:  
  
1.  Il programma e il thread che contengono il puntatore all'istruzione corrente può essere ottenuti dall'interfaccia di eventi.  
  
2.  L'IDE determina il file del codice sorgente corrente e la posizione, che viene visualizzata evidenziata nell'editor.  
  
3.  La sessione di debug in genere risponde a questo evento di arresto prima chiamando il programma **continua** metodo.  
  
4.  Quindi, il programma viene eseguito finché non viene rilevata una condizione di interruzione, ad esempio raggiunge un punto di interruzione, in cui la Germania case invia un evento punto di interruzione per la sessione di debug. L'evento punto di interruzione è un evento di arresto e la Germania è nuovo in attesa di una risposta dell'utente.  
  
5.  Se si sceglie di eseguire l'istruzione, in o da una funzione, l'IDE si comporta la sessione di debug per chiamare il programma `Step` metodo, passando l'unità di passaggio (istruzione, istruzione o riga) e il tipo di passaggio, vale a dire se eseguire l'istruzione, in , o dalla funzione. Una volta completato il passaggio, la Germania invia un evento di completamento del passaggio per la sessione di debug, ovvero un evento di arresto.  
  
     oppure  
  
     Se si sceglie di continuare l'esecuzione dal puntatore all'istruzione corrente, l'IDE si comporta la sessione di debug per chiamare il programma **Execute** metodo. Il programma riprende l'esecuzione finché incontra la condizione di interruzione successiva.  
  
     oppure  
  
     Se la sessione di debug per ignorare un evento di arresto particolare, la sessione di debug chiama il programma **continua** metodo. Se il programma è stato l'esecuzione di istruzioni in su o da una funzione quando si è verificato la condizione di interruzione, quindi continua il passaggio.  
  
 A livello di codice quando la Germania rileva una condizione di interruzione, invia tali eventi di arresto come [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) per la gestione di debug (SDM) di sessione per mezzo di un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfaccia. I passaggi di DE la [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) e [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfacce che rappresentano il programma e il thread che contiene il puntatore all'istruzione corrente. Le chiamate SDM [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per ottenere il frame superiore dello stack e chiama [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere il contesto di documento associato all'istruzione corrente puntatore. Il contesto di questo documento viene generalmente origine codice file name, riga e colonna. L'IDE li usa per evidenziare il codice sorgente che contiene il puntatore all'istruzione corrente.  
  
 Il SDM in genere risponde a questo evento di arresto prima chiamando [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Quindi il programma viene eseguito finché non viene rilevata una condizione di interruzione, ad esempio raggiunge un punto di interruzione, in cui invia i case di DE un [IDebugBreakpointEvent2 interfaccia](../../extensibility/debugger/reference/idebugbreakpointevent2.md) per il SDM. L'evento punto di interruzione è un evento di arresto e la Germania è nuovo in attesa di una risposta dell'utente.  
  
 Se si sceglie di eseguire l'istruzione, in o da una funzione, l'IDE si comporta SDM chiamare [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), passandogli il [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (istruzione, istruzione o riga) e [ STEPKIND](../../extensibility/debugger/reference/stepkind.md), vale a dire, se si desidera eseguire, su o dalla funzione. Una volta completato il passaggio, la Germania invia un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaccia SDM, il che è un evento di arresto.  
  
 Se si sceglie di continuare l'esecuzione dal puntatore all'istruzione corrente, l'IDE chiede SDM chiamare [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Il programma riprende l'esecuzione finché incontra la condizione di interruzione successiva.  
  
 Se il pacchetto di debug per ignorare un evento di arresto particolare, il pacchetto di debug chiama SDM, il quale vengono chiamate [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Se il programma è stato l'esecuzione di istruzioni in su o da una funzione quando si è verificato la condizione di interruzione, quindi continua il passaggio. Ciò implica che il programma gestisce uno stato di avanzamento nell'esecuzione, in modo che è in grado di continuare.  
  
 Le chiamate verso il SDM `Step`, **Execute**, e **continua** sono asincrona, il che significa che il SDM prevede la chiamata per restituire rapidamente. Se la Germania invia il SDM un evento di arresto sullo stesso thread prima `Step`, **Execute**, o **continua** viene restituito, si blocca la SDM.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)