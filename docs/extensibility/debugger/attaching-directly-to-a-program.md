---
title: Connessione direttamente a un programma | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c528925e323e4cff5784365e3097cc7f5f414963
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-directly-to-a-program"></a>Connessione direttamente a un programma
Gli utenti che desiderano eseguire il debug di programmi in un processo che è già in esecuzione in genere seguono questo processo:  
  
1.  Nell'IDE, scegliere il **processi di Debug** comando il **strumenti** menu.  
  
     Il **processi** viene visualizzata la finestra di dialogo.  
  
2.  Scegli un processo e fare clic su di **collegamento** pulsante.  
  
     Il **Connetti a processo** viene visualizzata la finestra di dialogo, l'elenco di tutti i motori di debug (DEs) installati nel computer.  
  
3.  Specificare la crittografia DEs da utilizzare per il debug del processo selezionato e quindi fare clic su **OK**.  
  
 Il pacchetto di debug, avvia una sessione di debug e passa l'elenco di DEs. La sessione di debug a sua volta passa questo elenco, insieme a una funzione di callback, per il processo selezionato e quindi chiede il processo per enumerare i programmi in esecuzione.  
  
 A livello di codice in risposta alla richiesta dell'utente, il pacchetto di debug crea un'istanza di gestore di sessione di debug (SDM) e passa l'elenco di DEs selezionato. L'elenco, il pacchetto di debug passa il SDM un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfaccia. Il pacchetto di debug passa l'elenco di DEs per il processo selezionato chiamando [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Chiama quindi il SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) sulla porta per enumerare i programmi in esecuzione nel processo.  
  
 Da questo momento, ogni motore di debug è collegato a un programma come descritto in dettaglio nella [collegamento dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md), con due eccezioni.  
  
 Per motivi di efficienza, DEs implementati per condividere uno spazio degli indirizzi con il SDM vengono raggruppati in modo che ogni Germania disponga di un gruppo di programmi si connetterà al. In questo caso, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) chiamate [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) e passa una matrice di programmi a cui connettersi.  
  
 La seconda eccezione è che gli eventi di avvio inviati da un DE la connessione a un programma che è già in esecuzione non includono in genere l'evento punto di ingresso.  
  
## <a name="see-also"></a>Vedere anche  
 [L'invio di eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)