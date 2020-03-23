---
title: Misurare l'utilizzo della memoria nelle app
description: È possibile rilevare perdite di memoria e memoria inefficiente mentre si sta eseguendo il debug con lo strumento di diagnostica integrato nel debugger.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2876e1b25380719a4424c5828c8b37fb5bb72b41
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "75929239"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Misurare l'utilizzo della memoria in Visual Studio

È possibile rilevare perdite di memoria e memoria inefficiente mentre si sta eseguendo il debug con lo strumento di diagnostica **Utilizzo memoria** integrato nel debugger. Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo per comprendere meglio l'impatto sull'utilizzo della memoria dei tipi di oggetti. È possibile raccogliere snapshot di app.NET, native o in modalità mista (.NET e native).

L'immagine seguente mostra la finestra **Strumenti di diagnostica**, disponibile in Visual Studio 2015 Update 1 e versioni successive:

![Aggiornamento di DiagnosticTools&#45;1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

Anche se è possibile raccogliere snapshot di memoria in qualsiasi momento nello strumento **Utilizzo memoria** è possibile usare il debugger di Visual Studio per controllare la modalità di esecuzione dell'applicazione durante l'analisi dei problemi di prestazioni. L'impostazione dei punti di interruzione, l'esecuzione di istruzioni, l'azione Interrompi tutto e altre azioni del debugger consentono di concentrare l'analisi delle prestazioni sui percorsi del codice più rilevanti. L'esecuzione di tali azioni durante l'esecuzione dell'app può eliminare il rumore dal codice che non interessa l'utente e può ridurre notevolmente la quantità di tempo necessaria per la diagnosi di un problema.

È inoltre possibile usare lo strumento di memoria all'esterno del debugger. Vedere [Utilizzo della memoria senza eseguire il debug](../profiling/memory-usage-without-debugging2.md). È possibile usare gli strumenti di profilatura senza il debugger collegato con Windows 7 e versioni successive. Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.

> [!NOTE]
> **Supporto dell'allocatore personalizzato** Il profiler della memoria nativa funziona raccogliendo i dati [dell'evento ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) di allocazione generati durante la fase di esecuzione.  Gli allocatori in CRT e Windows SDK sono stati annotati a livello di origine in modo che sia possibile acquisirne i dati di allocazione. Nella scrittura degli allocatori, fare in modo che qualsiasi funzione che restituisce un puntatore alla memoria heap appena allocata possa essere decorata con [__declspec](/cpp/cpp/declspec)(allocator), come illustrato in questo esempio per myMalloc:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Creare snapshot della memoria
> * Analizzare i dati di utilizzo della memoria

## <a name="collect-memory-usage-data"></a>Raccogliere i dati sull'utilizzo della memoria

1. Aprire il progetto per cui si vuole eseguire il debug in Visual Studio e impostare un punto di interruzione nell'app in corrispondenza del punto in cui si vuole iniziare a esaminare l'utilizzo della memoria.

    Se è presente un'area in cui si sospetta un problema di memoria, impostare il primo punto di interruzione prima che si verifichi tale problema.

    > [!TIP]
    > Poiché può essere difficile acquisire il profilo di memoria di un'operazione specifica quando l'app alloca e dealloca spesso la memoria, impostare punti di interruzione all'inizio e alla fine dell'operazione o eseguire i vari passaggi dell'operazione per trovare il punto esatto in cui l'utilizzo della memoria è cambiato.

2. Impostare un secondo punto di interruzione alla fine della funzione o dell'area di codice da analizzare o dopo un problema di utilizzo sospetto della memoria.

3. La finestra **Strumenti di diagnostica** viene visualizzata automaticamente, a meno che non sia stata disattivata. Per visualizzare nuovamente la finestra, fare clic su **Debug** > di**Windows** > **Mostra strumenti**di diagnostica .

4. Scegliere **Utilizzo memoria** con l'impostazione **Seleziona strumenti** sulla barra degli strumenti.

     ![Mostra strumenti di diagnostica](../profiling/media/diag-tools-select-tool-2.png "Strumento DiagToolsSelectTool")

5. Fare clic su **Debug / Avvia debug** (o **Avvia** sulla barra degli strumenti o **F5**).

     Al termine del caricamento dell'applicazione viene visualizzato il riepilogo degli strumenti di diagnostica.

     ![Scheda Riepilogo strumenti di diagnostica](../profiling/media/diag-tools-summary-tab-2.png "Scheda DiagToolsRiepilogoTab")

     > [!NOTE]
     > Poiché la raccolta di dati può influire sulle prestazioni di debug delle app native o in modalità mista, gli snapshot di memoria sono disattivati per impostazione predefinita. Per abilitare gli snapshot in app native o in modalità mista, avviare una sessione di debug (tasto di scelta rapida: **F5**). Quando viene visualizzata la finestra **Strumenti di diagnostica** , scegliere la scheda Utilizzo **memoria** , quindi **Profiling heap**.
     >
     >  ![Abilitare gli snapshot](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Stop (tasto di scelta rapida: **Maiusc**+**F5**) e riavviare il debug.

6. Per creare uno snapshot all'inizio della sessione di debug, scegliere **Crea snapshot** sulla barra degli strumenti di riepilogo **Utilizzo memoria**. Può essere utile impostare anche qui un punto di interruzione.

    ![Scatta un'istantanea](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Per creare una linea di base per i confronti di memoria, si consiglia di creare uno snapshot all'inizio di una sessione di debug.

6. Eseguire lo scenario in cui viene raggiunto il primo punto di interruzione.

7. Quando il debugger viene messo in pausa in corrispondenza del primo punto di interruzione, scegliere **Crea snapshot** sulla barra degli strumenti di riepilogo **Utilizzo memoria**.

8. Premere **F5** per eseguire l'applicazione fino al secondo punto di interruzione.

9. A questo punto, creare un altro snapshot.

     A questo punto, è possibile iniziare ad analizzare i dati.

## <a name="analyze-memory-usage-data"></a>Analizzare i dati di utilizzo della memoria
Nelle righe della tabella di riepilogo Utilizzo memoria sono elencati gli snapshot creati durante la sessione di debug e sono disponibili collegamenti a visualizzazioni più dettagliate.

![Tabella di riepilogo della memoria](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Il nome delle colonne dipende dalla modalità di debug selezionata nelle proprietà del progetto: .NET, nativa o mista (nativa e .NET).

- Le colonne **Oggetti (diff)** e **Allocazioni (diff)** visualizzano il numero di oggetti nella memoria .NET e nativa quando è stato creato lo snapshot.

- La colonna **Dimensioni heap (diff)** visualizza il numero di byte negli heap nativi e .NET

Quando si eseguono più snapshot, le celle della tabella di riepilogo includono la modifica del valore tra lo snapshot della riga e lo snapshot precedente.

Per analizzare l'utilizzo della memoria, fare clic su uno dei collegamenti che consente di visualizzare un report dettagliato dell'utilizzo della memoria:

- Per visualizzare i dettagli della differenza tra lo snapshot corrente e lo snapshot precedente, scegliere il collegamento di modifica a sinistra della freccia (![Aumento utilizzo memoria](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento dell'utilizzo della memoria")). Una freccia rossa indica un aumento nell'utilizzo della memoria, mentre una freccia verde indica una riduzione.

> [!TIP]
> Per identificare i problemi di memoria più rapidamente, i report diff vengono ordinati in base ai tipi di oggetto che sono aumentati maggiormente in termini di numero (fare clic sul collegamento di modifica nella colonna **Oggetti (diff)**) o di dimensioni complessive dell'heap (fare clic sul collegamento di modifica nella colonna **Dimensioni heap (diff)**).

- Per visualizzare i dettagli relativi solo allo snapshot selezionato, fare clic sul collegamento non di modifica.

   Il report verrà visualizzato in una finestra separata.

### <a name="managed-types-reports"></a>Report di tipi gestiti
 Scegliere il collegamento corrente di una cella **Oggetti (diff)** o **Allocazioni (diff)** nella tabella di riepilogo Utilizzo memoria.

 ![Debugger managed type report &#45; Paths to Root](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Il riquadro superiore mostra il numero e la dimensione dei tipi dello snapshot, inclusa la dimensione di tutti gli oggetti cui fa riferimento il tipo (**Dimensione inclusiva**).

 L'albero **Percorsi della radice** del riquadro inferiore mostra gli oggetti che fanno riferimento al tipo selezionato nel riquadro superiore. Il Garbage Collector di .NET Framework pulisce la memoria per un oggetto solo quando è stato rilasciato l'ultimo tipo cui fa riferimento.

 Nella struttura **Oggetti di riferimento** vengono visualizzati i riferimenti mantenuti dal tipo selezionato nel riquadro superiore.

 ![Visualizzazione report Oggetti referenziati gestiti](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Per visualizzare le istanze di un tipo selezionato nel riquadro superiore, scegliere l'icona ![Icona Istanza.](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon")

 ![Visualizzazione Istanze](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 La visualizzazione **Istanze** mostra le istanze dell'oggetto selezionato nello snapshot nel riquadro superiore. I riquadri **Percorsi della radice** e **Oggetti a cui si fa riferimento** mostrano gli oggetti che fanno riferimento all'istanza selezionata e i tipi a cui fa riferimento l'istanza selezionata. Quando il debugger viene arrestato nel punto in cui è stato creato lo snapshot, è possibile passare il mouse sulla cella **Valore** per visualizzare i valori dell'oggetto in una descrizione comandi.

### <a name="native-type-reports"></a>Report di tipo nativo
 Scegliere il collegamento corrente di una cella **Allocazioni (diff)** o **Dimensioni heap (diff)** della tabella di riepilogo Utilizzo memoria della finestra **Strumenti di diagnostica** .

 ![Visualizzazione di tipo nativo](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 La **Visualizzazione Tipi** mostra il numero e la dimensione dei tipi dello snapshot.

- Scegliere l'icona delle istanze![(icona dell'istanza nella colonna Tipo di](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")oggetto ) di un tipo selezionato per visualizzare informazioni sugli oggetti del tipo selezionato nello snapshot.

     La visualizzazione **Istanze** mostra ogni istanza del tipo selezionato. La selezione di un'istanza consente di visualizzare lo stack di chiamate che ha comportato la creazione dell'istanza nel riquadro **Stack di chiamate allocazione** .

     ![Visualizzazione Istanze](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Scegliere **Visualizzazione stack** dall'elenco **Modalità di visualizzazione** per visualizzare lo stack di allocazione per il tipo selezionato.

     ![Visualizzazione stack](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Report di modifica (Diff)

- Scegliere il collegamento di modifica in una cella della tabella di riepilogo della scheda **Utilizzo memoria** nella finestra **Strumenti di diagnostica** .

   ![Scegliere una modifica &#40;report&#41; diff](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Scegliere uno snapshot dall'elenco **Confronta con** di un report gestito o nativo.

   ![Scegliere uno snapshot dall'elenco Confronta con](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Il report di modifica aggiunge colonne (contrassegnate con **(Diff)**) al report di base che mostra la differenza tra il valore di snapshot di base e lo snapshot di confronto. Ecco un esempio di come potrebbe apparire un report delle differenze di visualizzazione del tipo nativo:

![Visualizzazione Diff tipi nativi](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Blog e video

[Analizzare CPU e memoria in fase di debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog di Visual C](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come raccogliere e analizzare i dati d'uso della memoria. Se è già stato completata la [presentazione del profiler](../profiling/profiling-feature-tour.md), è possibile vedere come analizzare l'uso della CPU nelle app di Windows.

> [!div class="nextstepaction"]
> [Analizzare l'utilizzo della CPU](../profiling/beginners-guide-to-performance-profiling.md)
