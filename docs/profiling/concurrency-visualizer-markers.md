---
title: Marcatori del visualizzatore di concorrenza.| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1e713292421613e835697037d5298a4a2c854f6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="concurrency-visualizer-markers"></a>Marcatori del visualizzatore di concorrenza
I marcatori del visualizzatore di concorrenza sono icone che rappresentano eventi in un'app.  In genere, l'applicazione genera questi eventi per definire fasi o occorrenze di un'applicazione.  Gli eventi possono essere generati dall'app o da librerie e runtime usati dall'app.  
  
## <a name="kinds-of-markers"></a>Tipi di marcatori  
 Il visualizzatore di concorrenza usa tre tipi di marcatori per rappresentare gli eventi dell'applicazione: flag, messaggi e span.  
  
1.  Usare un *flag* per indicare un punto di interesse nell'app.  Si potrebbe ad esempio usare un flag per indicare che un valore della variabile ha raggiunto una determinata soglia o che è stata generata un'eccezione.  
  
2.  Si può contrassegnare un momento anche con un *messaggio*. È tuttavia possibile usare questo tipo di marcatore per una traccia in stile log.  Ad esempio, quel che è stato copiato in un file di log può essere incluso in una chiamata di messaggio in modo che è sia possibile tenerne traccia e visualizzarlo nel visualizzatore di concorrenza. È anche possibile usare il visualizzatore di concorrenza per esportare questi dati in un file con estensione csv.  
  
3.  Uno *span* è un intervallo di tempo nell'app, ad esempio, una delle sue fasi.  
  
## <a name="marker-linkage-to-threads"></a>Collegamento di marcatori a thread  
 Per ogni thread che genera marcatori esiste un canale temporale separato.  L'ID del thread che genera gli eventi del marcatore viene visualizzato accanto alla descrizione del canale del marcatore.  L'ID visualizzato a sinistra del canale del marcatore corrisponde all'ID di un altro thread nel processo corrente.  
  
## <a name="marker-importance"></a>Importanza dei marcatori  
 Per i marcatori esistono quattro livelli di importanza: bassa, normale, alta e critica.  È possibile filtrare le origini dei marcatori in base al livello di importanza.  Ad esempio, se si vogliono vedere solo i marcatori di una determinata origine con importanza normale o critica, è possibile configurare il filtro nella finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). L'importanza di un marcatore viene visualizzata nella relativa descrizione comando e nel [rapporto marcatori](../profiling/markers-report.md).  
  
## <a name="marker-category"></a>Categoria dei marcatori  
 La categoria di un marcatore indica un gruppo di eventi marcatore che provengono dalla stessa origine.  Il visualizzatore di concorrenza usa i colori per distinguere le diverse categorie di flag e span. È possibile configurare il visualizzatore di concorrenza in modo che usi le categorie per filtrare gli eventi marcatore di un provider di eventi specifico.  Usare la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) per configurare il filtro.  
  
## <a name="known-sources-of-markers"></a>Origini note di marcatori  
 I marcatori possono essere generati da qualsiasi privider ETW purché il provider sia conforme a determinati vincoli. È possibile configurare il visualizzatore di concorrenza in modo che sia in ascolto di origini evento aggiuntive. Per impostazione predefinita, è in ascolto delle origini evento seguenti:  
  
-   [SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md)  
  
-   [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)  
  
-   [Flusso di dati](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)  
  
-   [Parallel LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)  
  
-   [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime)  
  
-   [Supporto per marcatori di scenario](http://msdn.microsoft.com/en-us/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
-   [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)  
  
 Nella finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) è possibile usare la scheda Marcatori per controllare se visualizzare nel visualizzatore di concorrenza i marcatori di varie origini e filtrare i marcatori in base a importanza e categoria.  
  
## <a name="markers-from-eventsource"></a>Marcatori di EventSource  
 Il visualizzatore di concorrenza può visualizzare anche eventi EventSource.  Per altre informazioni, vedere [Visualizing EventSource Events as Markers](../profiling/visualizing-eventsource-events-as-markers.md) (Visualizzazione di eventi EventSource come marcatori).  
  
## <a name="see-also"></a>Vedere anche  
 [Flag Markers](../profiling/flag-markers.md)  (Marcatori di flag)  
 [Message Markers](../profiling/message-markers.md)  (Marcatori di messaggio)  
 [Span Markers](../profiling/span-markers.md) (Marcatori di span)  
 [Visualizzazione di eventi EventSource come marcatori](../profiling/visualizing-eventsource-events-as-markers.md)