---
title: Analizzare l'utilizzo della memoria senza il debugger di Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b51d2be6e2ec45b55b04c906a9db71843c98f427
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="analyze-memory-usage-without-the-visual-studio-debugger"></a>Analizzare l'utilizzo della memoria senza il debugger di Visual Studio
È possibile usare lo strumento **Utilizzo memoria** senza debug per eseguire le operazioni seguenti:  
  
-   Monitorare l'uso della memoria delle tue app direttamente in Visual Studio mentre sviluppi uno scenario.  
  
-   Creare snapshot dettagliati dello stato della memoria dell'app.  
  
-   Confrontare snapshot per trovare la causa principale dei problemi di memoria.  
  
 Questo argomento descrive come usare lo strumento Utilizzo memoria per analizzare un'app XAML UWP. Se si vuole analizzare l'uso della memoria nelle app UWP che usano JavaScript e HTML, vedere [Analizzare l'utilizzo della memoria (JavaScript)](../profiling/javascript-memory.md).  
  
##  <a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a> Avviare una sessione di diagnostica con lo strumento Utilizzo memoria  
  
1.  Aprire un progetto universale di Windows C# in Visual Studio.  
  
2.  Nella barra dei menu scegliere **Debug/Profiler prestazioni...**.  
  
3.  Selezionare **Utilizzo memoria** e quindi scegliere il pulsante **Avvio** nella parte inferiore della pagina.  
  
     ![Avviare una sessione di diagnostica con lo strumento Utilizzo memoria](../profiling/media/memuse_start_diagnosticssession.png "MEMUSE_Start_DiagnosticsSession")  
  
##  <a name="BKMK_Monitor_memory_use"></a> Monitorare l'uso della memoria  
 Oltre a usare lo strumento **Utilizzo memoria** per generare rapporti dettagliati con cui trovare e correggere errori, è possibile usarlo anche per studiare gli effetti in tempo reale sulla memoria di uno scenario che si sta sviluppando attivamente.  
  
 Quando si avvia una sessione di diagnostica, l'app viene avviata e nella finestra **Strumenti di diagnostica** viene visualizzato un grafico della sequenza temporale dell'uso della memoria dell'app.  
  
 ![Pagina delle informazioni generali dello strumento Utilizzo memoria](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")  
  
 Il grafico della sequenza temporale mostra le fluttuazioni nella memoria dell'app durante la sua esecuzione. Eventuali picchi nel grafico in genere indicano che alcune stringhe di codice stanno raccogliendo o creando dati, per poi rimuoverli al termine del processo. Picchi significativi indicano aree che potrebbero essere ottimizzate. Più preoccupante sarebbe un aumento del consumo di memoria che non torna ai valori normali, perché può indicare un uso della memoria non efficiente o addirittura una perdita di memoria.  
  
###  <a name="BKMK_Close_a_monitoring_session"></a> Chiudere una sessione di monitoraggio  
 ![Arrestare la raccolta](../profiling/media/memuse__stopcollection.png "MEMUSE__StopCollection")  
  
 Per arrestare una sessione di monitoraggio senza creare un report, chiudi semplicemente la finestra di diagnostica. Per generare un rapporto dopo aver creato snapshot della memoria, scegliere **Arresta**.  
  
##  <a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a> Creare snapshot dello stato della memoria dell'app  
 Se viene riscontrato un problema di memoria su cui si vuole indagare, è possibile creare alcuni snapshot durante la sessione di diagnostica per acquisire oggetti in memoria in determinati momenti. Dato che un'app usa un gran numero di tipi di oggetti, potresti voler concentrare la tua analisi su un solo scenario. È anche una buona idea acquisire uno snapshot di base dell'app prima che si verifichi un problema di memoria, un altro dopo che il problema si presenta per la prima volta e uno o più snapshot aggiuntivi se si può ripetere lo scenario.  
  
 Per raccogliere snapshot, avvia una nuova sessione di diagnostica. Scegliere **Crea snapshot** quando si vogliono acquisire i dati di memoria. Per generare un rapporto, scegliere **Arresta**.  
  
##  <a name="BKMK_Memory_Usage_overview_page"></a> Pagina delle informazioni generali dello strumento Utilizzo memoria  
 Una volta completata la raccolta dei dati, lo strumento Utilizzo memoria arresta l'app e visualizza un report con informazioni generali.  
  
 ![Pagina delle informazioni generali dello strumento Utilizzo memoria](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")  
  
###  <a name="BKMK_Memory_Usage_snapshot_views"></a> Visualizzazioni snapshot dello strumento Utilizzo memoria  
 Usa le viste degli snapshot per aprire report dettagli in nuove finestre di Visual Studio. Esistono due tipi di viste degli snapshot:  
  
-   Un [rapporto dei dettagli degli snapshot](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports) mostra i tipi e le istanze in un solo snapshot.  
  
-   Un [rapporto delle differenze degli snapshot](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports) confronta i tipi e le istanze in due snapshot.  
  
 ![Link della visualizzazione Snapshot](../profiling/media/memuse__snapshotview_numbered.png "MEMUSE__SnapshotView_Numbered")  
  
 Gli elementi numerati nell'immagine della vista dello snapshot sono link che aprono viste di report di Utilizzo memoria.  
  
|||  
|-|-|  
|![Passaggio 1](../profiling/media/procguid_1.png "ProcGuid_1")|Il testo del link indica il numero totale di byte in memoria quando è stato creato lo snapshot.<br /><br /> Scegli questo link per visualizzare un report dettagli dello snapshot, ordinato in base alla dimensione totale delle istanze di tipo.|  
|![Passaggio 2](../profiling/media/procguid_2.png "ProcGuid_2")|Il testo del link indica il numero totale di oggetti in memoria quando è stato creato lo snapshot.<br /><br /> Scegli questo link per visualizzare un report dettagli dello snapshot, ordinato in base al numero di istanze dei tipi.|  
|![Passaggio 3](../profiling/media/procguid_3.png "ProcGuid_3")|Il testo del link indica la differenza tra la dimensione totale degli oggetti in memoria al momento dello snapshot e la dimensione totale dello snapshot precedente.<br /><br /> Il testo del link è un numero positivo quando la dimensione della memoria dello snapshot è maggiore rispetto allo snapshot precedente e un numero negativo quando la dimensione è minore. Il testo del link **Alla linea di base** indica che lo snapshot è il primo della sessione di diagnostica, mentre il testo **Nessuna differenza** indica che la differenza è zero.<br /><br /> Scegli questo link per visualizzare un report delle differenze degli snapshot, ordinato in base alla differenza riguardo alla dimensione totale delle istanze dei tipi.|  
|![Passaggio 4](../profiling/media/procguid_4.png "ProcGuid_4")|Il testo del link mostra la differenza tra il numero totale di oggetti di memoria nello snapshot e il numero di oggetti nello snapshot precedente.<br /><br /> Scegli questo link per visualizzare un report delle differenze degli snapshot, ordinato in base alla differenza riguardo al numero totale di istanze dei tipi.|  
  
##  <a name="BKMK_Snapshot_reports"></a> Rapporti degli snapshot  
 ![Rapporto snapshot dello strumento Utilizzo memoria](../profiling/media/memuse_snapshotreport_all.png "MEMUSE_SnapshotReport_All")  
  
###  <a name="BKMK_Snapshot_report_trees"></a> Alberi dei rapporti degli snapshot  
  
####  <a name="BKMK_Managed_Heap"></a> Heap gestito  
 L'albero dell'heap gestito [albero Heap gestito (dettagli di snapshot)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) e l'[albero Heap gestito (differenze di snapshot)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_) mostrano i tipi e le istanze presenti nel rapporto. Quando si seleziona un tipo o un'istanza, vengono visualizzati gli alberi **Percorsi della radice** e **Oggetti a cui si fa riferimento** per l'elemento selezionato.  
  
####  <a name="BKMK_Paths_to_Root"></a> Percorsi della radice  
 L'[albero Percorsi della radice (dettagli di snapshot)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) e l'[albero Percorsi della radice (differenze di snapshot)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_) mostrano la catena di oggetti che fanno riferimento al tipo o all'istanza. Garbage Collector di .NET Framework pulisce la memoria per un oggetto solo una volta rilasciati tutti i riferimenti.  
  
####  <a name="BKMK_Referenced_Objects"></a> Oggetti a cui si fa riferimento  
 L'[albero Oggetti a cui si fa riferimento (dettagli di snapshot)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) e l'[albero Oggetti a cui si fa riferimento (differenze di snapshot)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_) mostrano gli oggetti a cui fa riferimento l'istanza o il tipo selezionato.  
  
###  <a name="BKMK_Object_Type_and_Instance_fields"></a> Campi Tipo di oggetto e Istanza  
 Quando una voce **Tipo di oggetto** ha voci figlio, è possibile scegliere l'icona a forma di freccia per visualizzarle. Se il colore del testo **Tipo di oggetto** è blu, è possibile scegliere di passare all'oggetto nel suo file di codice sorgente. Il file di origine si apre in una finestra separata.  
  
 I nomi di istanza sono ID univoci generati dallo strumento Utilizzo memoria.  
  
 Se si nota un tipo che non risulta facilmente identificabile o se non si capisce in che modo sia interessato dal codice, probabilmente si tratta di un oggetto di .NET Framework, del sistema operativo o del compilatore visualizzato dallo strumento Utilizzo memoria perché coinvolto nelle catene di proprietà degli oggetti.  
  
###  <a name="BKMK_Report_tree_filters_"></a> Filtri degli alberi dei rapporti  
 La maggior parte delle app contiene un numero sorprendentemente elevato di tipi, molti dei quali sono irrilevanti per uno sviluppatore di app. Lo strumento **Utilizzo memoria** definisce due filtri utilizzabili per nascondere la maggior parte di questi tipi negli alberi **Heap gestito** e **Percorsi della radice**. Puoi anche filtrare un albero per nome di tipo.  
  
 ![Opzioni di ordinamento e filtro](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")  
  
####  <a name="BKMK_Filter"></a> Filtro  
 Immettere una stringa nella casella **Filtro** per limitare la visualizzazione dell'albero ai tipi che contengono il testo specificato. Il filtro non fa distinzione tra maiuscole e minuscole e riconosce la stringa specificata in ogni parte dei nomi di tipo.  
  
####  <a name="BKMK_Collapse_Small_Objects"></a> Comprimi oggetti piccoli  
 Quando questo filtro è applicato, i tipi per cui l'impostazione **Dimensione (byte)** è minore dello 0,5% della dimensione totale della memoria dello snapshot vengono nascosti nell'elenco **Heap gestito**.  
  
####  <a name="BKMK_Just_My_Code"></a> Just My Code  
 Il filtro **Just My Code** nasconde la maggior parte delle istanze generate da codice esterno. I tipi esterni sono di proprietà del sistema operativo o di componenti .NET Framework oppure sono generati dal compilatore.  
  
##  <a name="BKMK_Snapshot_details_reports"></a> Rapporti dettagli degli snapshot  
 Usa un report dettagli di uno snapshot per concentrarti su un solo snapshot di una sessione di diagnostica. Per aprire un report dettagli, scegli uno dei link in una visualizzazione snapshot, come mostrato nell'immagine. Entrambi i collegamenti aprono lo stesso rapporto e l'unica differenza è il tipo di ordinamento iniziale dell'albero **Heap gestito** nel rapporto. In entrambi i casi, puoi modificare il tipo di ordinamento dopo l'apertura del report.  
  
 ![Link al rapporto degli snapshot in una visualizzazione snapshot](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "MEMUSE_SnapshotView_SnapshotDetailsLinks")  
  
-   Il link **MB** ordina il rapporto in base alla colonna **Dimensione inclusiva (byte)**.  
  
-   Il link **Oggetti** ordina il rapporto in base alla colonna **Conteggio**.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Albero Heap gestito (dettagli di snapshot)  
 Nell'albero **Heap gestito** sono elencati i tipi di oggetti contenuti in memoria. Puoi espandere un nome di tipo per visualizzare le dieci istanze più grandi del tipo, ordinate in base alla dimensione. Quando si seleziona un tipo o un'istanza, vengono visualizzati gli alberi **Percorsi della radice** e **Oggetti a cui si fa riferimento** per l'elemento selezionato.  
  
 ![Albero Heap gestito](../profiling/media/memuse__snapshotdetails_managedheaptree.png "MEMUSE__SnapshotDetails_ManagedHeapTree")  
  
|||  
|-|-|  
|**Tipo di oggetto**|Nome dell'istanza di tipo o di oggetto.|  
|**Conteggio**|Numero di istanze di oggetto del tipo. Il numero è sempre 1 per un'istanza.|  
|**Dimensioni (byte)**|Per un tipo, dimensione di tutte le istanze del tipo nello snapshot della memoria, esclusa la dimensione degli oggetti contenuti nelle istanze.<br /><br /> Per un'istanza o un tipo, dimensione dell'oggetto, esclusa la dimensione degli oggetti contenuti nell'istanza. istanze.|  
|**Dimensione inclusiva (byte)**|Dimensione delle istanze del tipo o di una singola istanza, inclusa la dimensione degli oggetti contenuti.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Albero Percorsi della radice (dettagli di snapshot)  
 L'albero **Percorsi della radice** mostra la catena di oggetti che fanno riferimento al tipo o all'istanza. Garbage Collector di .NET Framework pulisce la memoria per un oggetto solo una volta rilasciati tutti i riferimenti.  
  
 ![Albero Percorsi della radice per Tipi](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "MEMUSE_SnapshotDetails_Type_PathsToRootTree")  
  
 Quando si visualizza un tipo nell'albero **Percorsi della radice**, il numero di oggetti dei tipi che contengono riferimenti al tipo viene visualizzato nella colonna **Conteggio riferimenti**. La colonna non è visualizzata quando analizzi un'istanza.  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Albero Oggetti a cui si fa riferimento (dettagli di snapshot)  
 L'albero **Oggetti a cui si fa riferimento** mostra gli oggetti a cui fa riferimento l'istanza o il tipo selezionato.  
  
 ![Albero Oggetti a cui si fa riferimento per le istanze](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Tipo di oggetto / Istanza**|Nome dell'istanza di tipo o di oggetto.|  
|**Dimensioni (byte)**|Per un tipo, dimensione di tutte le istanze del tipo, esclusa la dimensione degli oggetti contenuti nel tipo.<br /><br /> Per un'istanza, dimensione dell'oggetto, esclusa la dimensione degli oggetti contenuti nell'oggetto.|  
|**Dimensione inclusiva (byte)**|Dimensione totale delle istanze del tipo o dimensione dell'istanza, inclusa la dimensione degli oggetti contenuti.|  
  
##  <a name="BKMK_Snapshot_difference__diff__reports"></a> Rapporti delle differenze di snapshot  
 Un report delle differenze degli snapshot mostra le modifiche tra uno snapshot principale e lo snapshot creato immediatamente prima. Per aprire un report delle differenze, scegli uno dei link in una visualizzazione snapshot, come mostrato nell'immagine. Entrambi i collegamenti aprono lo stesso rapporto e l'unica differenza è il tipo di ordinamento iniziale dell'albero **Heap gestito** nel rapporto. Puoi modificare il tipo di ordinamento dopo l'apertura del report.  
  
 ![Link al rapporto delle differenze in una visualizzazione snapshot](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "MEMUSE_SnapshotView_SnapshotDiffLinks")  
  
-   Il link **MB** ordina il rapporto in base alla colonna **Dimensione inclusiva (byte)**.  
  
-   Il link **Oggetti** ordina il rapporto in base alla colonna **Conteggio**.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Albero Heap gestito (differenze di snapshot)  
 Nell'albero **Heap gestito** sono elencati i tipi di oggetti contenuti in memoria. Puoi espandere un nome di tipo per visualizzare le dieci istanze più grandi del tipo, ordinate in base alla dimensione. Quando si seleziona un tipo o un'istanza, vengono visualizzati gli alberi **Percorsi della radice** e **Oggetti a cui si fa riferimento** per l'elemento selezionato.  
  
 ![Albero Heap gestito per un tipo nel rapporto delle differenze](../profiling/media/memuse_snapshotdiff_type_heap.png "MEMUSE_SnapshotDiff_Type_Heap")  
  
 Si noti che le colonne **Conteggio**, **Dimensione (byte)** e **Dimensione inclusiva (byte)** sono state compresse nell'immagine.  
  
|||  
|-|-|  
|**Tipo di oggetto**|Nome dell'istanza di tipo o di oggetto.|  
|**Conteggio**|Numero di istanze di un tipo nello snapshot principale. Il valore di **Conteggio** è sempre 1 per un'istanza.|  
|**Diff. conteggio**|Per un tipo, differenza nel numero di istanze del tipo tra lo snapshot principale e quello precedente. Il campo è vuoto per un'istanza.|  
|**Dimensioni (byte)**|Dimensione degli oggetti nello snapshot principale, esclusa la dimensione degli oggetti contenuti negli oggetti. Per un tipo, **Dimensione (byte)** e **Dimensione inclusiva (byte)** corrispondono ai totali delle dimensioni delle istanze di tipo.|  
|**Diff. dimensione totale (byte)**|Per un tipo, differenza nella dimensione totale delle istanze del tipo tra lo snapshot principale e quello precedente, esclusa la dimensione degli oggetti contenuti nelle istanze. Il campo è vuoto per un'istanza.|  
|**Dimensione inclusiva (byte)**|Dimensione degli oggetti nello snapshot principale, inclusa la dimensione degli oggetti contenuti negli oggetti.|  
|**Differenza dimensioni inclusive (byte)**|Per un tipo, differenza nella dimensione di tutte le istanze del tipo tra lo snapshot principale e quello precedente, inclusa la dimensione degli oggetti contenuti negli oggetti. Il campo è vuoto per un'istanza.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Albero Percorsi della radice (differenza di snapshot)  
 L'albero **Percorsi della radice** mostra la catena di oggetti che fanno riferimento al tipo o all'istanza. Garbage Collector di .NET Framework pulisce la memoria per un oggetto solo una volta rilasciati tutti i riferimenti.  
  
 ![Albero Percorsi della radice per le istanze in una visualizzazione differenze](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "MEMUSE_SnapshotDiff_PathsToRoot_Instance_All")  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Albero Oggetti a cui si fa riferimento (differenza di snapshot)  
 L'albero **Oggetti a cui si fa riferimento** mostra gli oggetti a cui fa riferimento l'istanza o il tipo principale.  
  
 ![Albero Oggetti a cui si fa riferimento per le istanze](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Tipo di oggetto / Istanza**|Nome dell'istanza di tipo o di oggetto.|  
|**Dimensioni (byte)**|Per un'istanza, dimensione dell'oggetto nello snapshot principale, esclusa la dimensione degli oggetti contenuti nell'istanza.<br /><br /> Per un tipo, dimensione totale di tutte le istanze del tipo nello snapshot principale, esclusa la dimensione degli oggetti contenuti nell'istanza.|  
|**Dimensione inclusiva (byte)**|Dimensione degli oggetti nello snapshot principale, inclusa la dimensione degli oggetti contenuti negli oggetti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Memoria JavaScript](../profiling/javascript-memory.md)  
 [Profilatura in Visual Studio](../profiling/index.md)  
 [Tour delle funzionalità di profilatura](../profiling/profiling-feature-tour.md)  
 [Procedure consigliate per le prestazioni per app UWP scritte in C++, C# e Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)   
 [Diagnosing memory issues with the new Memory Usage Tool in Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=394706) (Diagnostica dei problemi di memoria con il nuovo strumento Utilizzo memoria in Visual Studio)