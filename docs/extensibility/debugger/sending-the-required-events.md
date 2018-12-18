---
title: Inviare gli eventi richiesti | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: deeffb814dacc58b1fb3a3f993203139d9b1a081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sending-the-required-events"></a>Inviare gli eventi richiesti
Utilizzare questa procedura per l'invio degli eventi necessari.  
  
## <a name="process-for-sending-required-events"></a>Processo per l'invio degli eventi necessari  
 Gli eventi seguenti sono necessari, in quest'ordine, la creazione di un tipo di debug del motore (DE) e collegarlo a un programma:  
  
1.  Inviare un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) oggetto evento al gestore di sessione di debug (SDM) quando viene inizializzata la Germania per il debug di uno o più programmi in un processo.  
  
2.  Quando il programma da sottoporre a debug è collegato, inviare un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) oggetto evento per il SDM. Questo evento può essere un evento di arresto, a seconda della progettazione di motore.  
  
3.  Se il programma viene collegato quando viene avviato il processo, inviare un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) oggetto evento SDM per notificare l'IDE di nuovo thread. Questo evento può essere un evento di arresto, a seconda della progettazione di motore.  
  
4.  Inviare un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oggetto evento SDM quando il programma in fase di debug è terminato il caricamento o quando viene completata la connessione al programma. Questo evento deve essere un evento di arresto.  
  
5.  Se viene avviata l'applicazione da sottoporre a debug, inviare un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) oggetto evento SDM quando sta per essere eseguita la prima istruzione del codice dell'architettura della fase di esecuzione. Questo evento è sempre un evento di arresto. Quando l'esecuzione di istruzioni nella sessione di debug, l'IDE viene arrestato su questo evento.  
  
> [!NOTE]
>  Molti linguaggi di usano gli inizializzatori globali o funzioni esterne precompilate (dalla libreria CRT o Main) all'inizio del codice. Se la lingua del programma di cui si esegue il debug è presente uno di questi tipi di elementi che precedono il punto di ingresso iniziale, quindi questo codice viene eseguito e viene inviato l'evento punto di ingresso quando l'utente del punto di ingresso, ad esempio **principale** o `WinMain`, è stato raggiunto.  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)