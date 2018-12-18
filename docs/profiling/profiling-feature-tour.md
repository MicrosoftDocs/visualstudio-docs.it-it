---
title: Panoramica delle funzionalità di profilatura | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12c10e06d1dcd789212b04b591f0165e118139b1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="profiling-feature-tour"></a>Panoramica delle funzionalità di profilatura

Visual Studio offre un'ampia gamma di strumenti di profilatura che consentono di diagnosticare diversi tipi di problemi di prestazioni in base al tipo di app.

Gli strumenti di profilatura a cui è possibile accedere durante una sessione di debug sono disponibili nella finestra Strumenti di diagnostica. La finestra Strumenti di diagnostica viene visualizzata automaticamente, a meno che non sia stata disattivata. Per visualizzare la finestra, fare clic su **Debug/Windows/Mostra strumenti di diagnostica**. Con finestra aperta è possibile selezionare gli strumenti per cui si vogliono raccogliere dati.

![Finestra Strumenti di diagnostica](../profiling/media/prof-tour-diagnostic-tools.png "Strumenti di diagnostica")

Durante il debug è possibile usare la finestra **Strumenti di diagnostica** per l'analisi della CPU e dell'uso della memoria e si possono visualizzare gli eventi che generano informazioni relative alle prestazioni.

![Visualizzazione di riepilogo di Strumenti diagnostici](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Riepilogo di Strumenti di diagnostica")

La finestra **Strumenti di diagnostica** è spesso il modo migliore per profilare le app, ma per le build di versione è anche possibile effettuare un'analisi dopo che l'app è terminata. Per altre informazioni sui diversi approcci, vedere [Esecuzione degli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Per informazioni sugli strumenti di profilatura supportati per i diversi tipi di app, vedere [Quale strumento si deve usare?](#tool_support_info).

## <a name="analyze-cpu-usage"></a>Analizzare l'utilizzo della CPU

L'uso dello strumento Utilizzo CPU è consigliabile per iniziare ad analizzare le prestazioni dell'applicazione. Lo strumento offre maggiori informazioni sulle risorse della CPU consumate dall'applicazione. Per una descrizione più dettagliata dello strumento Utilizzo CPU, vedere la [Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md).

Dalla visualizzazione **Riepilogo** di Strumenti di diagnostica scegliere **Abilita profilatura CPU** (è necessario essere in una sessione di debug).

![Abilita profilatura CPU in Strumenti di diagnostica](../profiling/media/prof-tour-enable-cpu-profiling.png "Strumenti di diagnostica - Abilita profilatura CPU")

Per usare lo strumento in modo più efficace, impostare due punti di interruzione nel codice, uno all'inizio e alla fine della funzione o dell'area di codice che si vuole analizzare. Esaminare i dati di profilatura durante la pausa in corrispondenza del secondo punto di interruzione.

La visualizzazione **Utilizzo CPU** contiene un elenco di funzioni ordinate in base a quelle in esecuzione da tempo, con la funzione di maggior durata in cima all'elenco. In questo modo è possibile sapere quali sono le funzioni in cui si verificano colli di bottiglia delle prestazioni.

![Visualizzazione Utilizzo CPU in Strumenti di diagnostica](../profiling/media/prof-tour-cpu-usage.png "Strumenti di diagnostica - Utilizzo CPU")

Fare doppio clic su una funzione a cui si è interessati per aprire una visualizzazione più dettagliata a tre riquadri in modalità "farfalla", con la funzione selezionata al centro della finestra, la funzione chiamante a sinistra e le funzioni chiamate a destra. La sezione **Corpo funzione** indica la quantità totale di tempo (e la percentuale di tempo) impiegata nel corpo della funzione, escluso il tempo dedicato alle funzioni chiamanti e chiamate. Questi dati consentono di valutare se la funzione stessa è un collo di bottiglia delle prestazioni.

![Visualizzazione in modalità "farfalla" delle funzioni chiamanti e chiamate in Strumenti di diagnostica](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Strumenti di diagnostica - Visualizzazione delle funzioni chiamanti e chiamate")

## <a name="analyze-memory-usage"></a>Analizzare l'uso della memoria

La finestra Strumenti di diagnostica consente inoltre di valutare l'uso della memoria nell'applicazione. Ad esempio, è possibile esaminare il numero e le dimensioni degli oggetti nell'heap. Per istruzioni più dettagliate per l'analisi della memoria, vedere [Analizzare l'uso della memoria](../profiling/memory-usage.md).

Per analizzare l'uso della memoria, è necessario creare almeno uno snapshot della memoria durante il debug. Spesso, il modo migliore per analizzare la memoria consiste nel creare due snapshot: il primo immediatamente prima di un sospetto problema di memoria e il secondo subito dopo che si è verificato un sospetto problema di memoria. È quindi possibile confrontare i due snapshot in una visualizzazione differenziale e vedere esattamente che cosa è cambiato.

![Creazione di uno snapshot in Strumenti di diagnostica](../profiling/media/prof-tour-take-snapshots.gif "Strumenti di diagnostica - Creazione di snapshot")

Quando si seleziona uno dei collegamenti con la freccia appare una visualizzazione differenziale dell'heap (una freccia rossa verso l'alto ![Aumento utilizzo memoria](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento utilizzo memoria") indica un numero di oggetti in aumento (sinistra) o dimensioni dell'heap in aumento (destra)). Se si sceglie il collegamento a destra, si ottiene una visualizzazione differenziale dell'heap ordinata in base agli oggetti che hanno contribuito di più all'aumento delle dimensioni dell'heap. Ciò consente di individuare i problemi di memoria. Ad esempio, nell'illustrazione riportata di seguito, i byte usati dagli oggetti `ClassHandlersStore` sono aumentati di 3.492 byte nel secondo snapshot.

![Visualizzazione differenziale dell'heap in Strumenti di diagnostica](../profiling/media/prof-tour-mem-usage-diff-heap.png "Strumenti di diagnostica - Visualizzazione differenziale dell'heap")

Se invece si fa clic sul collegamento a sinistra nella visualizzazione **Utilizzo memoria**, la visualizzazione dell'heap è organizzata in base al numero di oggetti. Gli oggetti di un tipo particolare il cui numero è aumentato maggiormente appaiono in cima all'elenco (ordinati in base alla colonna **Diff. conteggio**).

## <a name="examine-performance-events"></a>Esaminare gli eventi prestazioni

La visualizzazione **Eventi** in Strumenti di diagnostica consente di visualizzare diversi eventi che si verificano durante il debug, ad esempio l'impostazione di un punto di interruzione o un'operazione di esecuzione del codice. È possibile verificare informazioni quali la durata dell'evento, misurata da quando il debugger è stato messo pausa l'ultima volta o quando è stata avviata l'applicazione. Ad esempio, se ci si sposta nel codice (F10, F11), la visualizzazione **Eventi** indica la durata del runtime dell'applicazione dall'operazione del passaggio precedente al passaggio corrente.

![Visualizzazione degli eventi in Strumenti di diagnostica](../profiling/media/prof-tour-events.png "Strumenti di diagnostica - Visualizzazione degli eventi")

 > [!NOTE]
 > Gli utenti di Visual Studio Enterprise possono visualizzare anche gli [eventi IntelliTrace](../debugger/intellitrace.md) in questa scheda.

Gli stessi eventi sono visualizzati anche nell'editor di codice, che è possibile visualizzare come PerfTips.

![Panoramica profilatura PerfTips](../profiling/media/prof-tour-perf-tips.png "Panoramica profilatura PerfTips")

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Esaminare le prestazioni dell'interfaccia utente e gli eventi di accessibilità (UWP)

Nelle applicazioni UWP è possibile abilitare l'**analisi dell'interfaccia utente** nella finestra Strumenti di diagnostica. Lo strumento cerca i comuni problemi di prestazioni o accessibilità e li indica nella visualizzazione **Eventi** durante il debug. Le descrizioni degli eventi contengono informazioni che possono essere utili per risolvere i problemi.

![Visualizzazione degli eventi di analisi dell'interfaccia utente in Strumenti di diagnostica](../profiling/media/prof-tour-ui-analysis.png "Strumenti di diagnostica - Visualizzazione gli eventi di analisi dell'interfaccia utente")

## <a name="profile-release-builds-without-the-debugger"></a>Profilare build di rilascio senza il debugger

Gli strumenti di profilatura come Utilizzo CPU e Utilizzo memoria possono essere usati con il debugger (vedere le sezioni precedenti) oppure è possibile eseguire gli strumenti con il profiler delle prestazioni, progettato per l'analisi delle build di **rilascio**. Nel profiler delle prestazioni è possibile raccogliere informazioni di diagnostica durante l'esecuzione dell'applicazione e quindi esaminare le informazioni raccolte dopo l'interruzione dell'applicazione. Per altre informazioni sui diversi approcci, vedere [Esecuzione degli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

![Profiler delle prestazioni](../profiling/media/prof-tour-performance-profiler.png "Profiler delle prestazioni")

Aprire il profiler delle prestazioni scegliendo **Debug / Profiler prestazioni**.

La finestra consente di selezionare più strumenti di profilatura in alcuni scenari. Gli strumenti come Utilizzo CPU possono visualizzare dati complementari che agevolano l'analisi.

## <a name="analyze-resource-consumption-xaml"></a>Analizzare il consumo di risorse (XAML)

Nelle app XAML, ad esempio le app WPF desktop di Windows e le app UWP, è possibile analizzare il consumo di risorse usando lo strumento Sequenza temporale applicazione. È possibile ad esempio analizzare il tempo impiegato dall'applicazione per preparare i frame dell'interfaccia utente (layout e rendering), per soddisfare le richieste di rete e disco e in scenari come l'avvio dell'applicazione, il caricamento delle pagine e il ridimensionamento di Windows. Per usare lo strumento, scegliere **Sequenza temporale dell'applicazione** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario con un sospetto problema di consumo delle risorse e quindi scegliere **Arresta raccolta** per generare il report.

I framerate ridotti nel grafico della **velocità effettiva degli elementi visivi** possono corrispondere a problemi di visualizzazione che si riscontrano quando si esegue l'applicazione. Analogamente, i numeri elevati nell'**utilizzo dei thread di interfaccia utente** possono corrispondere a problemi di velocità di risposta dell'interfaccia utente. Nel report è possibile selezionare un periodo di tempo con un sospetto problema di prestazioni e quindi esaminare in dettaglio le attività del thread dell'interfaccia utente nella visualizzazione Dettagli sequenza temporale (riquadro inferiore).

![Strumento di profilatura Sequenza temporale applicazione](../profiling/media/prof-tour-application-timeline.gif "Panoramica delle funzionalità di profilatura - Sequenza temporale applicazione")

Nella visualizzazione Dettagli sequenza temporale è possibile trovare informazioni quali il tipo di attività (o elemento dell'interfaccia utente interessato) e la durata dell'attività. Ad esempio, nella figura un evento **Layout** per un controllo Grid impiega 57,53 ms.

Per altre informazioni, vedere [Sequenza temporale dell'applicazione](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analizzare l'uso della GPU (Direct3D)

Nelle applicazioni Direct3D (i componenti Direct3D devono essere in C++) è possibile esaminare l'attività sulla GPU e analizzare i problemi di prestazioni. Per altre informazioni, vedere l'articolo relativo all'[uso della GPU](../debugger/gpu-usage.md). Per usare lo strumento, scegliere **Utilizzo GPU** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario che interessa per la profilatura e quindi scegliere **Arresta raccolta** per generare un report.

Quando si seleziona un periodo di tempo nei grafici e si sceglie **Visualizza dettagli**, appare una visualizzazione dettagliata nel riquadro inferiore. Nella visualizzazione dettagliata è possibile esaminare l'entità dell'attività in corso in ogni CPU e GPU. Selezionare gli eventi nel riquadro inferiore per ottenere i popup nella sequenza temporale. Ad esempio, selezionare l'evento **Present** per visualizzare i popup delle chiamate **presenti**. Le linee verticali grigio chiaro di vsync possono essere usate come riferimento per capire se per determinate chiamate **presenti** non è stato eseguito il vsync. Deve esistere una chiamata **presente** tra ogni due vsync affinché l'applicazione esegua costantemente 60 FPS.

![Strumento di profilatura Utilizzo GPU](../profiling/media/prof-tour-gpu-usage.png "Finestra di dialogo dello strumento Utilizzo GPU")

È anche possibile usare i grafici per determinare se esistono colli di bottiglia delle prestazioni associati alla CPU o GPU.

## <a name="analyze-performance-javascript"></a>Analizzare le prestazioni (JavaScript)

Per le app UWP è possibile usare lo strumento Memoria JavaScript e lo strumento Velocità di risposta interfaccia utente HTML.

Lo strumento Memoria JavaScript è simile allo strumento Utilizzo memoria disponibile per altri tipi di applicazioni. È possibile usare questo strumento per comprendere in che modo viene usata la memoria e individuare le perdite di memoria nell'applicazione. Per maggiori dettagli sullo strumento, vedere [Memoria JavaScript](../profiling/javascript-memory.md).

![Strumento di profilatura Memoria JavaScript](../profiling/media/diagjsmemory.png "Finestra di dialogo dello strumento Memoria JavaScript")

Per diagnosticare la velocità di risposta dell'interfaccia utente, i tempi di caricamento lenti e gli aggiornamenti visivi lenti nelle app UWP, usare lo strumento Velocità di risposta interfaccia utente HTML. L'uso è simile a quello dello strumento Sequenza temporale dell'applicazione per altri tipi di applicazioni. Per altre informazioni, vedere [Velocità di risposta dell'interfaccia utente HTML](../profiling/html-ui-responsiveness.md).

![Strumento di profilatura Velocità di risposta interfaccia utente HTML](../profiling/media/diaghtmlresp.png "Finestra di dialogo dello strumento Velocità di risposta interfaccia utente HTML")

## <a name="analyze-network-usage-uwp"></a>Analizzare l'uso della rete (UWP)

Nelle app UWP è possibile analizzare le operazioni di rete eseguite con l'API `Windows.Web.Http`. Questo strumento può aiutare a risolvere i problemi relativi ad autenticazione e accesso, all'uso non corretto della cache e alle prestazioni insufficienti di visualizzazione download. Per usare lo strumento, scegliere **Rete** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario che usa `Windows.Web.Http` e quindi scegliere **Arresta raccolta** per generare il report.

![Strumento di profilatura Rete](../profiling/media/prof-tour-network-usage.png "Finestra di dialogo relativa all'utilizzo della rete")

Selezionare un'operazione nella visualizzazione di riepilogo per visualizzare altri dettagli.

![Informazioni dettagliate nello strumento Rete](../profiling/media/prof-tour-network-usage-details.png "Finestra di dialogo dei dettagli sull'utilizzo della rete")

Per altre informazioni, vedere [Utilizzo della rete](../profiling/network-usage.md).

## <a name="analyze-performance-legacy-tools"></a>Analizzare le prestazioni (strumenti precedenti)

Se sono necessarie funzionalità, ad esempio la strumentazione, che non sono attualmente presenti negli strumenti Utilizzo CPU o Utilizzo memoria e si eseguono applicazioni desktop o ASP.NET, è possibile usare Esplora prestazioni per la profilatura. Lo strumento non è supportato nelle app UWP. Per altre informazioni, vedere [Esplora prestazioni](../profiling/performance-explorer.md).

![Strumento Esplora prestazioni](../profiling/media/prof-tour-performance-explorer.png "Esplora prestazioni")

## <a name="tool_support_info"></a>Quale strumento si deve usare?  

Nella tabella seguente sono riportati i diversi strumenti offerti da Visual Studio e i diversi tipi di progetto con cui possono essere usati:
  
|Strumento di prestazioni|Desktop di Windows|UWP|ASP.NET/ASP.NET Core| 
|----------------------|---------------------|-------------|-------------|  
|[Utilizzo memoria](../profiling/memory-usage.md)|sì|sì|sì| 
|[Utilizzo CPU](../profiling/cpu-usage.md)|sì (vedere la nota)|sì|sì (vedere la nota)|
|[Utilizzo GPU](../debugger/gpu-usage.md)|sì|sì|No| 
|[Sequenza temporale applicazione](../profiling/application-timeline.md)|sì|sì|No|
|[PerfTips](../profiling/perftips.md)|sì|Sì per XAML, no per HTML|sì|
|[Esplora prestazioni](../profiling/performance-explorer.md)|sì|No|sì|
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|
|[Utilizzo della rete](../profiling/network-usage.md)|No|sì|No|
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|No|Sì per HTML, no per XAML|No| 
|[Memoria JavaScript](../profiling/javascript-memory.md)|No|Sì per HTML, no per XAML|No|

> [!NOTE]
> Per .NET Core e ASP.NET Core, lo strumento Utilizzo CPU non offre attualmente risultati accurati con i file PBD portabili. Usare invece file PDB completi.

## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)