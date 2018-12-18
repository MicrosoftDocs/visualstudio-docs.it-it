---
title: Visualizzazione Thread (prestazioni in parallelo) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccb86d36429f8695222f69fbf6d78635a338bfe5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="threads-view-parallel-performance"></a>Visualizzazione Thread (prestazioni in parallelo)
La **visualizzazione thread** è la visualizzazione più dettagliata e completa nel Visualizzatore di concorrenza (scegliere **Analizza** > **Visualizzatore di concorrenza** per avviare il visualizzatore di concorrenza). Tramite questa visualizzazione, è possibile identificare se i thread sono in esecuzione o se sono bloccati a causa di operazioni di sincronizzazione, di I/O oppure per altri motivi.  
  
 Durante l'analisi del profilo, il visualizzatore di concorrenza esamina tutti gli eventi di cambio di contesto del sistema operativo per ogni thread dell'applicazione. I cambi di contesto possono verificarsi per diversi motivi, ad esempio nei casi seguenti:  
  
-   Un thread è bloccato su una primitiva di sincronizzazione.  
  
-   Il quantum di un thread scade.  
  
-   Un thread esegue una richiesta di I/O di blocco.  
  
 Nella visualizzazione Thread viene assegnata una categoria a ogni cambio di contesto quando l'esecuzione di un thread si arresta. Le categorie vengono visualizzate nella legenda nella parte inferiore sinistra della visualizzazione. Il visualizzatore di concorrenza classifica gli eventi di cambio di contesto cercando nello stack di chiamate del thread le API di blocco conosciute. Se non viene rilevata alcuna corrispondenza nello stack di chiamate, viene usato il motivo di attesa fornito da [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]. Tuttavia, la categoria [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] può essere basata su un dettaglio di implementazione e potrebbe non riflettere lo scopo dell'utente. Ad esempio, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] segnala il motivo dell'attesa per il blocco in lettura-scrittura nativo come I/O anziché come sincronizzazione. Nella maggior parte dei casi è possibile identificare la causa principale di un evento di blocco esaminando gli stack di chiamate che corrispondono agli eventi di cambio di contesto.  
  
 La visualizzazione Thread mostra anche le dipendenze tra thread. Ad esempio, se si identifica un thread bloccato su un oggetto di sincronizzazione, è possibile cercare il thread che lo ha sbloccato ed è possibile esaminare l'attività nello stack di chiamate per il thread nel punto in cui ha sbloccato l'altro.  
  
 Quando i thread sono in esecuzione, il visualizzatore di concorrenza raccoglie campioni. Nella visualizzazione Thread è possibile analizzare quale codice viene eseguito da uno o più thread durante il segmento di esecuzione. È anche possibile esaminare i rapporti di blocco e i rapporti di profilatura dell'esecuzione dell'albero dello stack di chiamate.  
  
## <a name="usage"></a>Utilizzo  
 Ecco in che modo è possibile usare la visualizzazione Thread:  
  
-   Identificazione dei motivi per cui l'interfaccia utente di un'app non risponde durante alcune fasi di esecuzione.  
  
-   Identificazione della quantità di tempo trascorso in un blocco dovuto a sincronizzazione, I/O, errori di pagina e altri eventi.  
  
-   Identificazione del grado di interferenza da altri processi in esecuzione nel sistema.  
  
-   Identificazione dei problemi di bilanciamento del carico per l'esecuzione parallela.  
  
-   Identificazione delle cause di scalabilità non ottimale o assente, ad esempio i motivi per cui le prestazioni di un'app parallela non migliorano quando sono disponibili più core logici.  
  
-   Individuazione del livello di concorrenza nell'app, per agevolare la parallelizzazione.  
  
-   Individuazione delle dipendenze tra thread di lavoro e percorsi critici di esecuzione.  
  
## <a name="examining-specific-time-intervals-and-threads"></a>Analisi di intervalli di tempo specifici e thread  
 La visualizzazione Thread mostra una sequenza temporale. È possibile usare le funzionalità di zoom e panoramica all'interno della sequenza temporale per esaminare gli intervalli specifici e i thread dell'applicazione. Sull'asse x viene rappresentato il tempo mentre sull'asse y sono riportati diversi canali:  
  
-   Due canali di I/O per ogni unità disco del sistema, un canale per la lettura e uno per la scrittura.  
  
-   Un canale per ogni thread del processo.  
  
-   Canali dei marcatori, se nella traccia sono presenti eventi marcatori. I canali dei marcatori vengono inizialmente visualizzati sotto i canali di thread che hanno generato tali eventi.  
  
-   Canali GPU.  
  
 Di seguito è riportata un'immagine della visualizzazione Thread:  
  
 ![Visualizzazione dei thread](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
Visualizzazione Thread  
  
 Inizialmente i thread sono disposti nell'ordine in cui vengono creati, in modo che il thread dell'applicazione principale sia il primo. È possibile usare l'opzione di ordinamento nell'angolo in alto a sinistra della visualizzazione per ordinare i thread in base a un altro criterio (ad esempio, secondo i thread che svolgono la maggior quantità di operazioni di esecuzione).  
  
 È possibile nascondere i thread che non eseguono alcuna attività selezionandone i nomi nella colonna a sinistra e quindi scegliendo il pulsante **Nasconde i thread selezionati** nella barra degli strumenti. È consigliabile nascondere i thread che sono completamente bloccati perché le relative statistiche sono irrilevanti e potrebbero intasare i rapporti.  
  
 Per identificare altri thread da nascondere, nella legenda attiva scegliere il rapporto **Riepilogo per thread** nella scheda **Rapporto profilo**. Verrà visualizzato il grafico della suddivisione di esecuzione, che mostra lo stato dei thread per l'intervallo di tempo attualmente selezionato. Con alcuni livelli di zoom, alcuni thread potrebbero non essere visualizzati. In questo caso, vengono visualizzati puntini di sospensione a destra.  
  
 Dopo aver selezionato un intervallo di tempo e alcuni thread in esso contenuti, è possibile avviare l'analisi delle prestazioni.  
  
## <a name="analysis-tools"></a>Strumenti di analisi  
 Questa sezione descrive i rapporti e altri strumenti di analisi.  
  
### <a name="thread-blocking-details"></a>Dettagli sul blocco dei thread  
 Per ottenere informazioni su un evento di blocco in una determinata area di un thread, posizionare il puntatore su tale area per visualizzare una descrizione comando, che contiene informazioni come categoria, ora di inizio dell'area, durata del blocco e API di blocco, se presente. Se si seleziona l'area del blocco, nel riquadro inferiore verrà visualizzato lo stack in quel preciso momento, insieme alle stesse informazioni visualizzate nella descrizione comando. Esaminando lo stack di chiamate, è possibile determinare la causa sottostante per l'evento di blocco del thread. È possibile ottenere altre informazioni sui processi e sui thread selezionando il segmento ed esaminando la scheda Corrente.  
  
 Un percorso di esecuzione potrebbe avere più eventi di blocco. È possibile esaminarli per categoria di blocco in modo da identificare più rapidamente le aree problematiche. È sufficiente scegliere una delle categorie di blocco nella legenda a sinistra.  
  
### <a name="dependencies-between-threads"></a>Dipendenze tra thread  
 Il visualizzatore di concorrenza può visualizzare le dipendenze tra i thread del processo in modo da stabilire cosa stava tentando di eseguire un thread bloccato e ottenere informazioni su quale altro thread ne abbia abilitato l'esecuzione. Per determinare quale thread ha sbloccato un altro thread, selezionare il segmento di blocco rilevante. Se il visualizzatore di concorrenza è in grado di determinare il thread di sblocco, disegna una linea tra il thread di sblocco e il segmento di esecuzione che segue il segmento di blocco. Inoltre, la scheda **Stack di sblocco** mostra lo stack di chiamate rilevante.  
  
### <a name="thread-execution-details"></a>Dettagli sull'esecuzione dei thread  
 Nel grafico della sequenza temporale di un thread i segmenti verdi mostrano quando era in esecuzione il codice. È possibile ottenere informazioni più dettagliate su un segmento di esecuzione.  
  
 Quando si seleziona un punto in un segmento di esecuzione, il visualizzatore di concorrenza cerca tale punto nel tempo nello stack di chiamate rilevante e quindi visualizza un cursore nero sopra il punto selezionato nel segmento di esecuzione e lo stesso stack di chiamate viene visualizzato nella scheda **Stack corrente**. È possibile selezionare più punti nel segmento di esecuzione.  
  
> [!NOTE]
>  Il visualizzatore di concorrenza potrebbe non essere in grado di risolvere una selezione in un segmento di esecuzione. In genere, ciò si verifica quando la durata del segmento è inferiore a un millisecondo.  
  
 Per ottenere un profilo di esecuzione per tutti i thread abilitati (non nascosti) nell'intervallo di tempo attualmente selezionato, scegliere il pulsante **Esecuzione** nella legenda attiva.  
  
### <a name="timeline-graph"></a>Grafico della sequenza temporale  
 Il grafico della sequenza temporale mostra l'attività di tutti i thread nel processo e di tutti i dispositivi disco fisici nel computer host. Vengono inoltre visualizzati l'attività della GPU e gli eventi marcatori.  È possibile fare zoom avanti per visualizzare altri dettagli oppure zoom indietro per visualizzare un intervallo di tempo più lungo. È inoltre possibile selezionare dei punti nel grafico per ottenere dettagli sulle categorie, gli orari di avvio, le durate e gli stati dello stack di chiamate.  
  
 Nel grafico della sequenza temporale uno specifico colore indica lo stato di un thread in un determinato momento. Ad esempio, i segmenti verdi sono quelli in esecuzione, i segmenti rossi sono bloccati per la sincronizzazione, i segmenti gialli sono quelli con precedenza e i segmenti viola sono impegnati in operazioni di I/O del dispositivo. È possibile usare questa visualizzazione per esaminare il bilanciamento del lavoro tra i thread coinvolti in un ciclo parallelo o in attività simultanee. Se un thread richiede più tempo per il completamento rispetto agli altri, il lavoro potrebbe essere sbilanciato. È possibile usare queste informazioni per migliorare le prestazioni del programma distribuendo il lavoro in modo più uniforme tra i thread.  
  
 Se in un determinato momento solo un thread è verde (in esecuzione), l'app potrebbe non sfruttare completamente la concorrenza nel sistema. È possibile usare il grafico della sequenza temporale per esaminare le dipendenze tra thread e le relazioni temporali tra i thread di blocco e quelli bloccati. Per riordinare i thread, selezionare un thread e quindi nella barra degli strumenti scegliere il pulsante freccia su o freccia giù. Per nascondere i thread, selezionarli e quindi scegliere il pulsante **Nascondi thread**.  
  
### <a name="profile-reports"></a>Rapporti dei profili  
 Sotto il grafico della sequenza temporale sono visualizzati un profilo della sequenza temporale e un riquadro con schede per vari rapporti. I rapporti si aggiornano automaticamente quando si cambia la visualizzazione Thread. Per le tracce di grandi dimensioni, il riquadro dei rapporti potrebbe non essere disponibile mentre gli aggiornamenti vengono calcolati. Ogni rapporto dispone di due regolazioni di filtro: Riduzione rumore e Just My Code. Usare Riduzione rumore per filtrare le voci dell'albero delle chiamate in cui viene impiegata una quantità di tempo limitata. Il valore predefinito del filtro è 2%, ma può essere impostato qualsiasi valore compreso tra 0% e 99%. Per visualizzare solo l'albero delle chiamate per il codice, selezionare la casella di controllo **Just My Code**. Per visualizzare tutti gli alberi delle chiamate, deselezionarla.  
  
#### <a name="profile-report"></a>Rapporto profili  
 Questa scheda mostra i rapporti corrispondenti alle voci nella legenda attiva. Per visualizzare un rapporto, scegliere una delle voci.  
  
#### <a name="current-stack"></a>Stack corrente  
 Questa scheda mostra lo stack di chiamate per un punto selezionato su un segmento di thread nel grafico della sequenza temporale. Gli stack di chiamate vengono tagliati per mostrare solo l'attività correlata al programma.  
  
#### <a name="unblocking-stack"></a>Stack di sblocco  
 Per vedere quale thread ha sbloccato il thread selezionato e in corrispondenza di quale riga di codice, scegliere la scheda **Stack di sblocco**.  
  
#### <a name="execution"></a>Esecuzione  
 Il rapporto di esecuzione riporta la suddivisione del tempo che l'applicazione ha impiegato nell'esecuzione.  
  
 Per trovare la riga di codice in cui è trascorso il tempo di esecuzione, espandere l'albero delle chiamate e quindi scegliere **Visualizza origine** o **Visualizza siti di chiamata** dal menu di scelta rapida per la voce dell'albero delle chiamate. **Visualizzazione origine** consente di individuare la riga di codice eseguita. **Visualizza siti di chiamata** permette di individuare la riga di codice che ha chiamato la riga di codice eseguita. Se esiste un solo sito di chiamata, la riga di codice corrispondente è evidenziata. Se sono presenti più siti di chiamata, è possibile selezionare quello desiderato nella finestra di dialogo visualizzata e quindi scegliere il pulsante **Vai a origine** per evidenziare il codice del sito di chiamata. È spesso molto utile individuare il sito di chiamata con il maggior numero di istanze, i tempi più elevati o entrambi. Per altre informazioni, vedere [Rapporto Profilo di esecuzione](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Sincronizzazione  
 Il rapporto di sincronizzazione mostra le chiamate responsabili dei blocchi di sincronizzazione, insieme ai tempi di blocco aggregati di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di sincronizzazione](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>I/O  
 Il rapporto di I/O mostra le chiamate responsabili dei blocchi di I/O, insieme ai tempi di blocco aggregati di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di I/O (visualizzazione Thread)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>Sleep  
 Il rapporto di sospensione mostra le chiamate responsabili dei blocchi di sospensione, insieme ai tempi di blocco aggregati di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di sospensione](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Gestione della memoria  
 Il rapporto di gestione della memoria mostra le chiamate in cui si sono verificati blocchi di gestione della memoria, insieme ai tempi di blocco aggregati di ogni stack di chiamate. È possibile usare queste informazioni per identificare le aree che presentano problemi notevoli di paging o di Garbage Collection.  Per altre informazioni, vedere [Tempo di gestione della memoria](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Precedenza  
 Il rapporto di precedenza mostra le istanze in cui i processi nel sistema hanno avuto la precedenza sul processo corrente e i singoli thread che hanno sostituito i thread nel processo corrente. È possibile usare queste informazioni per identificare i processi e i thread maggiormente responsabili della precedenza. Per altre informazioni, vedere [Tempo di precedenza](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>Elaborazione interfaccia utente  
 Il rapporto di elaborazione interfaccia utente mostra le chiamate responsabili dei blocchi di elaborazione dell'interfaccia utente, insieme ai tempi di blocco aggregati di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di elaborazione dell'interfaccia utente](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Riepilogo per thread  
 Questa scheda mostra una visualizzazione a colonne di colori diversi del tempo totale trascorso da ciascun thread nell'esecuzione, nel blocco, nell'I/O e in altri stati. Le colonne sono etichettate nella parte inferiore. Quando si modifica il livello di zoom nel grafico della sequenza temporale, questa scheda viene aggiornata automaticamente. Con alcuni livelli di zoom, alcuni thread potrebbero non essere visualizzati. In questo caso, vengono visualizzati puntini di sospensione a destra. Se il thread desiderato non è presente, è possibile nascondere gli altri thread. Per altre informazioni, vedere [Rapporto di riepilogo per thread](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Operazioni su disco  
 Questa scheda mostra i processi e i thread coinvolti in operazioni di I/O su disco per conto del processo corrente, i file interessati (ad esempio, le DLL che sono state caricate), il numero di byte letti e altre informazioni. È possibile usare questo rapporto per valutare il tempo impiegato nell'accesso ai file durante l'esecuzione, specialmente se il processo sembra presentare vincoli di I/O. Per altre informazioni, vedere [Rapporto delle operazioni su disco](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)