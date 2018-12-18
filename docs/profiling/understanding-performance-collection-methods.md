---
title: Informazioni sui metodi di raccolta delle prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd5a584402473d9576376d6357dd67e6c47f391c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="understanding-performance-collection-methods"></a>Informazioni sui metodi di raccolta delle prestazioni

Gli strumenti di profilatura di Visual Studio forniscono cinque metodi che è possibile usare per raccogliere dati sulle prestazioni. In questo argomento vengono descritti i diversi metodi e vengono suggeriti alcuni scenari in cui può risultare appropriata la raccolta dei dati con un particolare metodo.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).

|Metodo|Descrizione|
|------------|-----------------|
|[Campionamento](#sampling)|Raccoglie dati statistici sulle operazioni eseguite da un'applicazione.|
|[Strumentazione](#instrumentation)|Raccoglie informazioni dettagliate sugli intervalli per ogni chiamata di funzione.|
|[Concorrenza](#concurrency)|Raccoglie informazioni dettagliate sulle applicazioni multithread.|
|[Memoria .NET](#net_memory)|Raccoglie informazioni dettagliate sull'allocazione e la Garbage Collection della memoria .NET.|
|[Interazioni tra livelli](#tier_interaction)|Raccoglie informazioni sulle chiamate di funzione ADO.NET sincrone a un database di SQL Server.<br /><br /> I dati di profilatura dell'interazione tra livelli possono essere raccolti usando qualsiasi edizione di Visual Studio, ma possono essere visualizzati solo in Visual Studio Enterprise.|

Usando alcuni metodi di profilatura, è anche possibile raccogliere dati aggiuntivi, ad esempio i contatori delle prestazioni di hardware e software. Per altre informazioni, vedere [Raccolta di dati aggiuntivi relativi alle prestazioni](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a> Campionamento

Il metodo di profilatura di campionamento raccoglie dati statistici sulle operazioni eseguite da un'applicazione durante l'esecuzione di una profilatura. Il metodo di campionamento è leggero e ha un impatto minimo sull'esecuzione dei metodi dell'applicazione.

Il campionamento è il metodo predefinito degli strumenti di profilatura di Visual Studio. È utile per le operazioni seguenti:

- Analisi iniziali delle prestazioni dell'applicazione.
- Analisi dei problemi di prestazioni che comportano l'uso del processore (CPU).

Il metodo di profilatura di campionamento interrompe il processore del computer a intervalli prestabiliti e raccoglie lo stack di chiamate della funzione. I conteggi dei campioni esclusivi vengono incrementati per la funzione in esecuzione e i conteggi inclusivi vengono incrementati per tutte le funzioni chiamanti nello stack di chiamate. I report di campionamento presentano i totali di questi conteggi per il modulo, la funzione, la riga del codice sorgente e l'istruzione sottoposti a profilatura.

Per impostazione predefinita, il profiler imposta l'intervallo di campionamento sui cicli della CPU. È possibile modificare il tipo di intervallo su un altro contatore delle prestazioni della CPU e impostare il numero di eventi del contatore per l'intervallo. È anche possibile raccogliere dati di profilatura di interazione tra livelli (TIP), che forniscono informazioni sulle query eseguite su un database SQL server tramite ADO.NET.

[Raccolta di statistiche sulle prestazioni tramite il campionamento](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)

[Sampling Method Data Views](../profiling/profiler-sampling-method-data-views.md) (Visualizzazioni dei dati del metodo di campionamento)

## <a name="instrumentation"></a> Strumentazione

Il metodo di profilatura della strumentazione raccoglie informazioni dettagliate sugli intervalli per le chiamate di funzione in un'applicazione sottoposta a profilatura. La profilatura della strumentazione è utile per le operazioni seguenti:

- Analisi dei colli di bottiglia di input/output, ad esempio attività di I/O su disco.
- Analisi di un particolare modulo o set di funzioni.

Il metodo di strumentazione inserisce codice in un file binario che acquisisce informazioni sugli intervalli per ogni funzione nel file instrumentato e ogni chiamata di funzione effettuata da tali funzioni. La strumentazione identifica inoltre il momento in cui una funzione esegue una chiamata al sistema operativo per operazioni quali la scrittura in un file. I report di strumentazione usano quattro valori per rappresentare il tempo totale impiegato in una funzione o una riga del codice sorgente:

- Inclusivo trascorso - Tempo totale impiegato per l'esecuzione della funzione o della riga del codice sorgente.

- Inclusivo applicazione - Tempo impiegato per l'esecuzione della funzione o della riga del codice sorgente, escluso il tempo trascorso in chiamate al sistema operativo.

- Esclusivo trascorso - Tempo impiegato per l'esecuzione del codice nel corpo della funzione o della riga del codice sorgente. È escluso il tempo impiegato per l'esecuzione di funzioni chiamate dalla funzione o dalla riga del codice sorgente.

- Esclusivo applicazione - Tempo impiegato per l'esecuzione del codice nel corpo della funzione o della riga del codice sorgente. È escluso il tempo impiegato per l'esecuzione di chiamate al sistema operativo e il tempo impiegato per l'esecuzione delle funzioni chiamate dalla funzione o dalla riga del codice sorgente.

È inoltre possibile raccogliere i contatori delle prestazioni sia della CPU che del software usando il metodo di strumentazione.

[Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md)

[Raccolta di dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a> Concorrenza

La profilatura della concorrenza raccoglie informazioni sulle applicazioni multithread. La profilatura dei conflitti di risorse raccoglie informazioni dettagliate sullo stack di chiamate ogni volta che thread concorrenti sono obbligati ad attendere l'accesso a una risorsa condivisa. La visualizzazione della concorrenza raccoglie inoltre informazioni più generali sulla modalità di interazione dell'applicazione multithread con se stessa, l'hardware, il sistema operativo e altri processi nel computer host:

- I report sui conflitti di risorse visualizzano il numero totale di conflitti e il tempo totale trascorso in attesa di una risorsa per i moduli, le funzioni, le righe del codice sorgente e le istruzioni in cui si è verificata l'attesa. I grafici della sequenza temporale mostrano inoltre quando si sono verificati i conflitti.

- Il visualizzatore di concorrenza mostra informazioni grafiche che è possibile usare per individuare problemi relativi a colli di bottiglia delle prestazioni, sottoutilizzo della CPU, conflitti di thread, migrazione di thread, ritardi di sincronizzazione, aree di I/O sovrapposte e per ottenere altre informazioni. Quando possibile, l'output grafico fornisce collegamenti allo stack di chiamate e ai dati del codice sorgente. I dati di visualizzazione della concorrenza possono essere raccolti solo per la riga di comando e le applicazioni Windows.

[Informazioni sui valori dei dati su conflitti di risorse](../profiling/understanding-resource-contention-data-values.md)

[Raccolta di dati di concorrenza di thread e processi](../profiling/collecting-thread-and-process-concurrency-data.md)

[Visualizzazioni dei dati su conflitti tra risorse](../profiling/resource-contention-data-views.md)

[Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)

## <a name="net_memory"></a> Memoria .NET

Il metodo di profilatura dell'allocazione della memoria .NET interrompe il processore del computer a ogni allocazione di un oggetto .NET Framework in un'applicazione sottoposta a profilatura. Quando vengono raccolti anche dati sulla durata degli oggetti, il profiler interrompe il processore dopo ogni operazione di Garbage Collection di .NET Framework.

Il profiler raccoglie informazioni sul tipo, la dimensione e il numero degli oggetti che sono stati creati in un'allocazione o eliminati in un'operazione di Garbage Collection.

- Quando si verifica un evento di allocazione, il profiler raccoglie informazioni aggiuntive sullo stack di chiamate della funzione. I conteggi di allocazione esclusivi vengono incrementati per la funzione attualmente in esecuzione e i conteggi inclusivi vengono incrementati per tutte le funzioni chiamanti nello stack di chiamate. I report .NET presentano i totali di questi conteggi per i tipi, i moduli, le funzioni, le righe del codice sorgente e le istruzioni sottoposti a profilatura.

- Quando si verifica una Garbage Collection, il profiler raccoglie dati sugli oggetti che sono stati eliminati e informazioni sugli oggetti in ogni generazione di Garbage Collection. Al termine dell'esecuzione della profilatura, il profiler registra i dati sugli oggetti che non sono stati eliminati in modo esplicito. Il report Durata oggetti mostra i totali per ogni tipo che è stato allocato durante l'esecuzione della profilatura.

La profilatura della memoria .NET può essere usata in modalità di campionamento o di strumentazione. La modalità selezionata non influisce sui report Allocazione e Durata oggetti che sono univoci per la profilatura della memoria .NET:

- Quando si esegue la profilatura della memoria .NET in modalità di campionamento, il profiler .NET usa gli eventi di allocazione della memoria come intervallo e visualizza il numero di oggetti allocati e i byte totali allocati come valori inclusivi ed esclusivi nei report.

- Quando si esegue la profilatura della memoria .NET in modalità di strumentazione, vengono raccolte informazioni dettagliate sugli intervalli insieme ai valori inclusivi ed esclusivi dell'allocazione.

[Informazioni sull'allocazione di memoria e i valori dei dati di durata di un oggetto](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)

## <a name="tier_interaction"></a> Interazioni tra livelli

La profilatura di interazione tra livelli aggiunge informazioni a un file di dati di profilatura sulle chiamate [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] sincrone tra una pagina [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o un'altra applicazione e un database [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. I dati includono il numero e l'ora delle chiamate e i tempi massimi e minimi. I dati di interazione tra livelli possono essere aggiunti ai dati di profilatura raccolti con i metodi di campionamento, strumentazione, memoria .NET o concorrenza.

![Dati di profilatura di interazione tra livelli](../profiling/media/tierinteraction_profilingtools.png "TierInteraction_ProfilingTools")

Dati di interazione tra livelli raccolti dagli strumenti di profilatura

[Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)

[Visualizzazioni Interazioni tra livelli](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Vedere anche

[Procedura: Raccogliere dati sulle prestazioni per un sito Web](../profiling/how-to-collect-performance-data-for-a-web-site.md)  
[Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)