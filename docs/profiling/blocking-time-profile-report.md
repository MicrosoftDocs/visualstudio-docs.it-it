---
title: Rapporto profili del tempo di blocco | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.report.blocking
helpviewer_keywords: Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 748b547cda2a3c07ed84337d37f2a7e096ee112d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="blocking-time-profile-report"></a>Report del profilo di durata del blocco
I rapporti profili contengono dati aggregati relativi al tempo di blocco per gli stack di chiamate specifici di ogni categoria di blocco, ad esempio "I/O" o "Sincronizzazione". Il rapporto Precedenza elenca i processi che precedevano il processo corrente con il numero di istanze di precedenza. Per compilare il rapporto profili di blocco, lo strumento raccoglie chiamate API di blocco e le accumula in un albero degli stack di chiamate. I dati visualizzati in questi rapporti variano in base all'intervallo di tempo corrente, ai thread nascosti e ai seguenti due filtri che possono essere applicati:  
  
-   Se l'opzione Just My Code è selezionata, vengono presentati solo gli stack frame con codice utente, più un livello sotto il codice utente.  
  
-   Se è impostato il valore di riduzione del rumore, gli stack fascicolati con una frequenza minore di quella specificata vengono ignorati.  
  
 Espandere qualsiasi voce dell'albero delle chiamate per individuare la riga di codice in cui viene impiegato il tempo di blocco. Per individuare la riga di codice sorgente per una voce, scegliere **Visualizza origine** nel relativo menu di scelta rapida. Per individuare la riga di codice che ha chiamato questa riga, scegliere **Visualizza siti di chiamata** nel menu di scelta rapida. Se solo un sito di chiamata è disponibile, il comando si connette alla riga di codice evidenziata per il sito di chiamata. Se sono disponibili più siti di chiamata, il comando apre una finestra di dialogo in cui è possibile selezionare una voce e quindi scegliere il pulsante **Passa all'origine** per individuare il sito di chiamata evidenziato. Spesso è molto utile visualizzare il codice sorgente per il sito di chiamata con il maggior numero di istanze, i tempi più elevati o entrambi.  
  
## <a name="blocking-time-report-columns"></a>Colonne del rapporto del tempo di blocco  
 Nella tabella seguente sono riportate le colonne per ogni rapporto del tempo di blocco.  
  
|Nome colonna|Descrizione|  
|-----------------|-----------------|  
|nome|Nome della funzione per ogni livello dello stack di chiamate.|  
|Istanze|Numero di istanze della chiamata di blocco per il periodo di tempo visibile.|  
|Tempo inclusivo di blocco|Tempo di blocco totale impiegato per tutti gli stack con rollup a questo livello dell'albero degli stack di chiamate. Il numero inclusivo è la somma del tempo esclusivo di blocco per questa funzione e del tempo esclusivo di blocco per tutti i relativi nodi figlio.|  
|Tempo esclusivo di blocco|Tempo di blocco totale impiegato in cui questa funzione è il livello più basso dello stack di chiamate. Una voce univoca dello stack di chiamate con un tempo esclusivo di blocco elevato può essere una funzione di interesse.|  
|API/Categoria di attesa|Visualizzata solo per le funzioni al livello più basso dello stack di chiamate. Se la firma della chiamata di blocco viene riconosciuta, viene specificato il nome dell'API di blocco. Se la firma non viene riconosciuta, vengono specificate le informazioni segnalate dal kernel.|  
|Dettagli|Nome completo della funzione. Include il conteggio delle righe, se disponibile.|  
  
### <a name="synchronization"></a>Sincronizzazione  
 Il rapporto Sincronizzazione specifica le chiamate responsabili dei segmenti di blocco nel tempo di sincronizzazione e i tempi di blocco aggregati di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di sincronizzazione](../profiling/synchronization-time.md)  
  
### <a name="sleep"></a>Sleep  
 Il rapporto Sospensione specifica le chiamate responsabili del tempo di blocco attribuito al tempo trascorso in modalità di sospensione e i tempi di blocco aggregati di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di sospensione](../profiling/sleep-time.md).  
  
### <a name="io"></a>I/O  
 Il rapporto I/O specifica le chiamate responsabili dei segmenti di blocco nel tempo di I/O e i tempi di blocco aggregati di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di I/O (visualizzazione Thread)](../profiling/i-o-time-threads-view.md).  
  
### <a name="memory-management"></a>Gestione della memoria  
 Il rapporto Gestione della memoria specifica le chiamate responsabili dei segmenti di blocco nelle operazioni di gestione della memoria e i tempi di blocco aggregati di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di gestione della memoria](../profiling/memory-management-time.md).  
  
### <a name="preemption"></a>Precedenza  
 Il rapporto Precedenza elenca i processi che precedevano il processo corrente insieme al numero di istanze.  È possibile espandere ogni processo per visualizzare i thread specifici che hanno sostituito i thread nel processo corrente e per visualizzare una suddivisione delle istanze di precedenza per ogni thread. Questo rapporto di blocco consente di eseguire meno azioni rispetto agli altri poiché la precedenza di solito viene imposta al processo dal sistema operativo, non da un problema nel codice. Per altre informazioni, vedere [Tempo di precedenza](../profiling/preemption-time.md).  
  
### <a name="ui-processing"></a>Elaborazione interfaccia utente  
 Il rapporto relativo all'elaborazione dell'interfaccia utente indica le chiamate responsabili dei segmenti di blocco nei blocchi di elaborazione dell'interfaccia utente, oltre ai tempi di blocco aggregati di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di elaborazione dell'interfaccia utente](../profiling/ui-processing-time.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Threads View](../profiling/threads-view-parallel-performance.md) (Visualizzazione Thread)