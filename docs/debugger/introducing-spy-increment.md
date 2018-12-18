---
title: Introduzione a Spy + + | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 826ef03bcca176d095c2110ed14227bb5faa2dbd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="introducing-spy"></a>Introduzione a Spy++
Spy++ consente di eseguire le attività seguenti:  
  
-   Visualizzare una struttura grafica delle relazioni tra gli oggetti di sistema, inclusi [processi](../debugger/processes-view.md), [thread](../debugger/threads-view.md)e [finestre](../debugger/windows-view.md).  
  
-   Cercare le [finestre](../debugger/how-to-search-for-a-window-in-windows-view.md), i [thread](../debugger/how-to-search-for-a-thread-in-threads-view.md), i [processi](../debugger/how-to-search-for-a-process-in-processes-view.md)o i [messaggi](../debugger/how-to-search-for-a-message-in-messages-view.md)specificati.  
  
-   Visualizzare le proprietà delle [finestre](../debugger/how-to-display-window-properties.md), dei [thread](../debugger/how-to-display-thread-properties.md), dei [processi](../debugger/how-to-display-process-properties.md)o dei [messaggi](../debugger/how-to-display-message-properties.md)selezionati.  
  
-   Selezionare una finestra, un thread, un processo o un messaggio direttamente nella visualizzazione.  
  
-   Usare lo [strumento di ricerca](../debugger/how-to-use-the-finder-tool.md) per selezionare una finestra tramite posizionamento del puntatore del mouse.  
  
-   Impostare [opzione messaggi](../debugger/how-to-open-messages-view-from-find-window.md) utilizzando i parametri di selezione del log dei messaggi complessi.  
  
 In Spy++ sono disponibili una barra degli strumenti e collegamenti ipertestuali che consentono un uso più rapido. Sono inoltre presenti un comando **Aggiorna** per aggiornare la visualizzazione attiva, uno **strumento di ricerca finestre** per facilitare il controllo e una finestra di dialogo **Tipo di carattere** per personalizzare le finestre di visualizzazione. Inoltre, Spy++ consente di salvare e ripristinare le preferenze dell'utente.  
  
 In diverse finestre di Spy++ è possibile fare clic con il pulsante destro del mouse per visualizzare un menu di scelta rapida dei comandi usati di frequente. I comandi visualizzati dipendono dalla posizione del puntatore. Se, ad esempio, si fa clic con il pulsante destro del mouse su una voce nella visualizzazione finestra e la finestra selezionata è visibile, è sufficiente scegliere **Evidenzia** dal menu di scelta rapida per fare in modo che il bordo della finestra selezionata lampeggi e sia così più facilmente identificabile.  
  
> [!NOTE]
>  Sono disponibili altre due utilità simili a Spy++, ossia PView, che mostra i dettagli relativi a processi e thread, e DDESPY.EXE, che consente di monitorare i messaggi di DDE (Dynamic Data Exchange).  
  
## <a name="64-bit-operating-systems"></a>Sistemi operativi a 64 bit  
 Sono disponibili due versioni di Spy++. La prima, denominata Spy++ (spyxx.exe), è stata progettata per visualizzare i messaggi inviati a una finestra in esecuzione in un processo a 32 bit. Ad esempio, Visual Studio viene eseguito in un processo a 32 bit. Pertanto, è possibile usare Spy++ per visualizzare i messaggi inviati a **Esplora soluzioni**. Poiché la configurazione predefinita per la maggior parte delle compilazioni in Visual Studio deve essere eseguito in un processo a 32 bit, questa prima versione di Spy + + è quella che [disponibile nel **strumenti** menu](../debugger/how-to-start-spy-increment.md) in Visual Studio.  
  
 La seconda versione, denominata Spy++ (64 bit) (spyxx_amd64.exe), è stata progettata per visualizzare i messaggi inviati a una finestra in esecuzione in un processo a 64 bit. Ad esempio, in un sistema operativo a 64 bit, il Blocco note viene eseguito in un processo a 64 bit. Pertanto, è possibile usare Spy++ (64 bit) per visualizzare i messaggi inviati al Blocco note. Spy++ (64 bit) si trova in genere in  
  
 .. \\ *Cartella di installazione di visual Studio*\Common7\Tools\spyxx_amd64.exe..  
  
 È possibile eseguire entrambe le versioni di Spy++ direttamente dalla riga di comando.  
  
> [!NOTE]
>  Anche se il nome del file di Spy++ (64 bit) contiene "amd", viene eseguito in qualsiasi sistema operativo Windows x64.  
  
## <a name="see-also"></a>Vedere anche 
 [Procedura: avviare Spy + +](../debugger/how-to-start-spy-increment.md)   
 [Utilizzo di Spy + +](../debugger/using-spy-increment.md)   
 [Visualizzazioni di Spy + +](../debugger/spy-increment-views.md)   
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)