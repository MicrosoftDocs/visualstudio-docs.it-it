---
title: L'invio di eventi di avvio dopo un avvio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 65e05d7da2acf5bd3eaf8dab1e3781d3d5b244a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sending-startup-events-after-a-launch"></a>L'invio di eventi di avvio dopo un avvio
Una volta collegato il motore di debug (DE) al programma, invia una serie di eventi di avvio alla sessione di debug  
  
 Gli eventi di avvio inviati nuovamente alla sessione di debug includono:  
  
-   Un evento di creazione del motore.  
  
-   Un evento di creazione del programma.  
  
-   Eventi di caricamento moduli e di creazione del thread.  
  
-   Un evento di completamento carico, inviato quando il codice è caricato e pronto per l'esecuzione, ma prima che venga eseguito qualsiasi codice  
  
    > [!NOTE]
    >  Quando si continua, questo evento vengono inizializzate le variabili globali ed eseguire routine di avvio.  
  
-   Possibili altri thread di creazione e eventi di caricamento moduli.  
  
-   Un evento punto di ingresso, che segnala che il programma ha raggiunto il punto di ingresso principale, ad esempio **Main** o `WinMain`. Questo evento non viene inviato in genere se la Germania associa a un programma che è già in esecuzione.  
  
 A livello di codice, prima di tutto la Germania invia gestore di sessione di debug (SDM) un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaccia che rappresenta un evento di creazione del motore, seguito da un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , che rappresenta un evento di creazione del programma.  
  
 In genere è seguito da uno o più [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) gli eventi di creazione di thread e [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) eventi di caricamento moduli.  
  
 Quando il codice è caricato e pronto per l'esecuzione, ma prima che venga eseguito qualsiasi codice, la Germania invia il SDM un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) evento di caricamento completo. Infine, se il programma non è già in esecuzione, la Germania invia un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) evento punto di ingresso, significa che il programma ha raggiunto il punto di ingresso principale e pronta per il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo di esecuzione](../../extensibility/debugger/control-of-execution.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)