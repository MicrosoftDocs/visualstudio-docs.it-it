---
title: Visualizzazione messaggi | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31baccc88b25979dfc92fed6217bec3b0ef16a55
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="messages-view"></a>Visualizzazione messaggi
Ogni finestra è presente un flusso di messaggi associati. Questo flusso di messaggi viene visualizzata una finestra di visualizzazione di messaggi. Vengono visualizzati gli handle di finestra, codice del messaggio e messaggio. È possibile creare una visualizzazione di messaggi per un thread o processo. Ciò consente di visualizzare i messaggi inviati a tutte le finestre di proprietà di un determinato processo o thread, è particolarmente utile per l'acquisizione di messaggi di inizializzazione della finestra.  
  
 Di seguito è riportata una tipica finestra di visualizzazione di messaggi. Si noti che la prima colonna contiene l'handle di finestra e la seconda colonna contiene un codice del messaggio (illustrato in [codici di messaggio](../debugger/message-codes.md)). Messaggio decodificato parametri e valori restituiti sono a destra.  
  
 ![Spy&#43; &#43; la visualizzazione messaggi](../debugger/media/spy--_messagesview.png "Spy + + _MessagesView")  
Visualizzazione messaggi di Spy++  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Per aprire una visualizzazione di messaggi per una finestra di un processo o thread  
  
1.  Spostare lo stato attivo per un [Windows Vista](../debugger/windows-view.md), [visualizzazione processi](../debugger/processes-view.md), o [visualizzazione thread](../debugger/threads-view.md) finestra.  
  
2.  Trovare il nodo per l'elemento di cui si desidera esaminare i messaggi e selezionarlo.  
  
3.  Dal **Spy** menu, scegliere **messaggi di Log**.  
  
     Il [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md) apre.  
  
4.  Selezionare le opzioni per il messaggio da visualizzare.  
  
5.  Premere **OK** per iniziare la registrazione messaggi.  
  
     Una viene visualizzata la finestra di visualizzazione di messaggi e **messaggi** menu viene aggiunto alla barra degli strumenti di Spy + +. A seconda delle opzioni selezionate, i messaggi di avviare il flusso nella finestra di visualizzazione di messaggi attiva.  
  
6.  Quando un numero sufficiente di messaggi, scegliere **Arresta registrazione** dal **messaggi** menu.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Controllo della visualizzazione messaggi](../debugger/how-to-control-messages-view.md)  
 Viene illustrato come gestire la visualizzazione messaggi.  
  
 [Apertura della visualizzazione messaggi dalla finestra Trova](../debugger/how-to-open-messages-view-from-find-window.md)  
 Viene illustrato come aprire la visualizzazione messaggi nella finestra di dialogo Trova finestra.  
  
 [Ricerca di un messaggio nella visualizzazione messaggi](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Viene illustrato come trovare un messaggio specifico nella visualizzazione dei messaggi.  
  
 [Avvio e arresto di visualizzazione del Log dei messaggi](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Viene illustrato come avviare e arrestare la registrazione dei messaggi.  
  
 [Codici di messaggio](../debugger/message-codes.md)  
 Definisce i codici per i messaggi elencati nella visualizzazione dei messaggi.  
  
 [Visualizzazione delle proprietà del messaggio](../debugger/how-to-display-message-properties.md)  
 Come visualizzare ulteriori informazioni su un messaggio.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)  
 Vengono illustrate le visualizzazioni ad albero Spy + + di windows, i messaggi, thread e processi.  
  
 [Uso di Spy++](../debugger/using-spy-increment.md)  
 Vengono presentati lo strumento Spy + + e come può essere usato.  
  
 [Finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md)  
 Consente di selezionare quali messaggi sono elencati nella visualizzazione messaggi attiva.  
  
 [Finestra di dialogo Ricerca messaggi](../debugger/message-search-dialog-box.md)  
 Utilizzato per trovare il nodo di un messaggio specifico nella visualizzazione dei messaggi.  
  
 [Finestra di dialogo Proprietà messaggio](../debugger/message-properties-dialog-box.md)  
 Consente di visualizzare le proprietà di un messaggio selezionato nella visualizzazione dei messaggi.  
  
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)  
 Include le sezioni che descrivono ogni Spy + + menu e finestra di dialogo.