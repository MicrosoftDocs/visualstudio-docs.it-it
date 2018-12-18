---
title: Visualizza i thread nel Debugger | Documenti Microsoft
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec5cdf340002c9f454c67b170b4e849360de0166
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="view-threads-in-the-debugger-in-visual-studio-using-the-threads-window"></a>Visualizza i thread nel debugger di Visual Studio usando la finestra thread
Nel **thread** finestra, è possibile esaminare e utilizzare i thread nell'applicazione sottoposta a debug. Per istruzioni dettagliate su come utilizzare il **thread** finestra, vedere [procedura dettagliata: eseguire il Debug utilizzando la finestra thread](../debugger/how-to-use-the-threads-window.md).
  
 Il **thread** finestra contiene una tabella in cui ogni riga rappresenta un thread nell'applicazione. Per impostazione predefinita, nella tabella sono elencati tutti i thread dell'applicazione, ma è possibile filtrare l'elenco per visualizzare solo i thread che interessano. Ogni colonna contiene un tipo di informazioni diverso. È possibile inoltre nascondere alcune colonne. Visualizzando tutte le colonne, vengono visualizzate le informazioni seguenti da sinistra verso destra:  
  
-   La colonna del contrassegno, dove è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione. Per informazioni su come contrassegnare un thread, vedere [come: Flag e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   Il thread colonna corrente, in cui una freccia gialla indica che il thread corrente (una struttura freccia indica il contesto di debug corrente per un thread non corrente).
  
-   Il **ID** colonna che contiene il numero di identificazione per ogni thread.  
  
-   Il **ID gestito** colonna che contiene i numeri di identificazione gestiti per i thread gestiti.  
  
-   Il **categoria** colonna che classifica i thread come thread di interfaccia utente, i gestori delle chiamate a procedura remota o thread di lavoro. Una categoria speciale identifica il thread principale dell'applicazione.  
  
-   Il **nome** colonna che identifica ogni thread in base al nome, se presente, o come \<No Name >.  
  
-   Il **percorso** colonna, che mostra in cui il thread è in esecuzione. È possibile espandere questo percorso per visualizzare lo stack di chiamate completo per il thread.  
  
-   Il **priorità** colonna che contiene la priorità o precedenza assegnata dal sistema per ogni thread.  
  
-   Il **Affinity Mask** colonna, ovvero una colonna avanzata (in genere nascosta). In questa colonna viene visualizzata la maschera di affinità del processore per ogni thread. In un sistema con più processori, la maschera di affinità determina in quali processori è possibile eseguire un thread.  
  
-   Il **numero sospesi** colonna (in genere nascosto), che contiene il conteggio sospeso e in genere è nascosta. Questo conteggio determina se un thread può essere eseguito. Per una spiegazione del conteggio sospeso, vedere "Blocco e sblocco dei thread" più avanti in questo argomento.  
  
-   Il **nome processo** colonna (in genere nascosto), che contiene il processo a cui appartiene ogni thread. Questa colonna può essere utile quando si esegue il debug di più processi.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Per visualizzare la finestra Thread in modalità di interruzione o di esecuzione  
  
-   Durante il debug, selezionare il **Debug** dal menu **Windows**, quindi fare clic su **thread**.  
  
### <a name="to-display-or-hide-a-column"></a>Per visualizzare o nascondere una colonna  
  
-   Nella barra degli strumenti nella parte superiore del **thread** finestra, fare clic su **colonne**, quindi selezionare o deselezionare il nome della colonna che si desidera visualizzare o nascondere.    

## <a name="display-flagged-threads"></a>Visualizzare i thread con flag  
 È possibile contrassegnare un thread che si desidera prestare particolare attenzione mediante un'icona nella **thread** finestra. Per ulteriori informazioni, vedere [come: Flag e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md). Nel **thread** finestra è possibile scegliere di visualizzare tutti i thread o solo i thread con flag.  
  
#### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
-   Scegliere il **Mostra solo con flag thread** pulsante nella parte superiore del **thread** finestra. (Se visualizzato in grigio, è necessario contrassegnare un thread prima.) 

## <a name="freeze-and-thaw-threads"></a>Bloccare e sbloccare i thread  
 Quando si blocca un thread, l'esecuzione dello stesso da parte del sistema non viene avviata anche se le risorse sono disponibili.  
  
 Nel codice nativo, è possibile sospendere o riprendere i thread chiamando le funzioni di Windows `SuspendThread` e `ResumeThread` o le funzioni MFC [CWinThread:: SuspendThread](/cpp/mfc/reference/CWinThread-class.md#cwinthread__suspendthread) e [CWinThread:: ResumeThread](/cpp/mfc/reference/CWinThread-class.md#cwinthread__resumethread). Se si chiama `SuspendThread` o `ResumeThread`, si modifica il *numero sospesi*, che viene visualizzato il **thread** finestra. Tuttavia, se si blocca o sblocca un thread nativo, il numero sospesi non viene modificato. Nel codice nativo, un thread non può essere eseguito a meno che non sia sbloccato e il numero sospesi non sia pari a zero.  
  
 Nel codice gestito, il blocco o lo sblocco di un thread comporta la modifica del numero sospesi. Nel codice gestito, un thread bloccato presenta un numero sospesi pari a 1. Nel codice nativo, un thread bloccato presenta un numero sospesi pari a 0 a meno che non sia stato sospeso tramite una chiamata a `SuspendThread`.  
  
> [!NOTE]
>  Quando si esegue il debug di una chiamata da codice nativo a codice gestito, il codice gestito viene eseguito nello stesso thread fisico del codice nativo che lo ha chiamato. Sospendendo o bloccando l'esecuzione del thread di codice nativo si otterrà anche il blocco del codice gestito.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Per bloccare o sbloccare l'esecuzione di un thread  
  
-   Nella barra degli strumenti nella parte superiore del **thread** finestra, fare clic su **Blocca thread** o **Sblocca thread**.  
  
     Questa azione influisce solo sui thread selezionati nel **thread** finestra. 

### <a name="switch-to-another-thread"></a>Passare a un altro thread 

Una freccia gialla indica il thread corrente (e la posizione del puntatore di esecuzione). Una freccia verde ricurva indica che un thread non correnti è il contesto di debug corrente.

#### <a name="to-switch-to-another-thread"></a>Per passare a un altro thread  
  
-   Effettuare uno dei passaggi seguenti:  
  
    -   Fare doppio clic su un thread.  
  
    -   Fare doppio clic su un thread e fare clic su **passa al Thread**.

## <a name="group-and-sort-threads"></a>Thread di ordinamento e di gruppo  
 Quando si raggruppano i thread, nella tabella viene visualizzata un'intestazione per ogni gruppo. L'intestazione contiene una descrizione del gruppo, ad esempio "Thread di lavoro" o "Thread senza flag", e un controllo di struttura ad albero. I thread membro di ciascuno gruppo appaiono sotto l'intestazione del gruppo. Per nascondere i thread membro di un gruppo, è possibile utilizzare il controllo di struttura ad albero per comprimere il gruppo.  
  
 Poiché il raggruppamento ha la precedenza sull'ordinamento, è possibile ad esempio raggruppare i thread per categoria, per poi ordinarli in base all'ID all'interno di ogni categoria.  
  
#### <a name="to-sort-threads"></a>Per ordinare i thread  
  
1.  Nella barra degli strumenti nella parte superiore del **thread** finestra, fare clic sul pulsante nella parte superiore di qualsiasi colonna.  
  
     I thread verranno ordinati in base ai valori in quella colonna.  
  
2.  Per invertire l'ordine, fare nuovamente clic sullo stesso pulsante.  
  
     I thread che prima erano visualizzati all'inizio dell'elenco appariranno al fondo.  
  
#### <a name="to-group-threads"></a>Per raggruppare i thread  
  
-   Nel **thread** degli strumenti della finestra, fare clic su di **raggruppare** elenco, quindi fare clic sui criteri che si desidera raggruppare i thread.  
  
#### <a name="to-sort-threads-within-groups"></a>Per ordinare i thread all'interno di gruppi  
  
1.  Nella barra degli strumenti nella parte superiore del **thread** finestra, fare clic su di **raggruppare** elenco, quindi fare clic sui criteri che si desidera raggruppare i thread.  
  
2.  Nel **thread** finestra, fare clic sul pulsante nella parte superiore di qualsiasi colonna.  
  
     I thread verranno ordinati in base ai valori in quella colonna.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Per espandere o comprimere tutti i gruppi  
  
-   Nella barra degli strumenti nella parte superiore del **thread** finestra, fare clic su **Espandi gruppi** o **Comprimi gruppi**.  
  
## <a name="search-for-specific-threads"></a>Cercare thread specifici  
 In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] è possibile cercare i thread che corrispondono a una stringa specificata. Quando si cercano i thread nel **thread** , la finestra Visualizza tutti i thread che corrispondono alla stringa di ricerca in qualsiasi colonna. Informazioni includono il percorso del thread che viene visualizzato nella parte superiore dello stack di chiamate di **percorso** colonna. Per impostazione predefinita, tuttavia, lo stack di chiamate completo non viene cercato.  
  
#### <a name="to-search-for-specific-threads"></a>Per cercare thread specifici  
  
-   Nella barra degli strumenti nella parte superiore del **thread** finestra, passa al **ricerca** casella e:  
  
    -   Digitare una stringa di ricerca, quindi premere INVIO.  
  
         \- oppure -  
  
    -   Fare clic sull'elenco di riepilogo a discesa accanto al **ricerca** e selezionare una stringa di ricerca da una ricerca precedente.  
  
-   (Facoltativo) Per includere lo stack di chiamate completo nella ricerca, selezionare **Cerca nello Stack**.   
  
## <a name="display-thread-call-stacks-and-switching-between-frames"></a>Visualizzare gli stack di chiamate di Thread e passaggio da un frame  
In un programma multithread ogni thread dispone di un proprio stack di chiamate. Il **thread** finestra fornisce un modo pratico per visualizzare questi stack.

> [!TIP]
> Per una rappresentazione visiva dello stack di chiamate per ogni thread, utilizzare il [stack in parallelo](../debugger/get-started-debugging-multithreaded-apps.md) finestra.
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Per visualizzare lo stack di chiamate di un thread  
  
-   Nel **percorso** colonna, fare clic sul triangolo invertito accanto al percorso del thread.  
  
     Il percorso si espanderà per visualizzare lo stack di chiamate del thread.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Per visualizzare o comprimere gli stack di chiamate di tutti i thread  
  
-   Nella barra degli strumenti nella parte superiore del **thread** finestra, fare clic su **Espandi stack di chiamate** o **Comprimi stack di chiamate**.  
  
## <a name="see-also"></a>Vedere anche  
 [Il debug di applicazioni a thread multipli](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Introduzione al debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md)