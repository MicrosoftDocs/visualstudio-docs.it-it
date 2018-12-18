---
title: Analizzare l'utilizzo della memoria in Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d6fc25c3a9d7306332c704453f22073df4e76546
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="profile-memory-usage-in-visual-studio"></a>Profilare l'utilizzo della memoria in Visual Studio
È possibile rilevare perdite di memoria e memoria inefficiente mentre si sta eseguendo il debug con lo strumento di diagnostica **Utilizzo memoria** integrato nel debugger. Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo per comprendere meglio l'impatto sull'utilizzo della memoria dei tipi di oggetti. È possibile raccogliere snapshot di app.NET, native o in modalità mista (.NET e native).  
  
 L'immagine seguente mostra la finestra **Strumenti di diagnostica**, disponibile in Visual Studio 2015 Update 1 e versioni successive:  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
 Anche se è possibile raccogliere snapshot di memoria in qualsiasi momento nello strumento **Utilizzo memoria** è possibile usare il debugger di Visual Studio per controllare la modalità di esecuzione dell'applicazione durante l'analisi dei problemi di prestazioni. L'impostazione dei punti di interruzione, l'esecuzione di istruzioni, l'azione Interrompi tutto e altre azioni del debugger consentono di concentrare l'analisi delle prestazioni sui percorsi del codice più rilevanti. L'esecuzione di tali azioni durante l'esecuzione dell'app può eliminare il rumore dal codice che non interessa l'utente e può ridurre notevolmente la quantità di tempo necessaria per la diagnosi di un problema.  
  
 È inoltre possibile usare lo strumento di memoria all'esterno del debugger. Vedere [Memory Usage without Debugging](../profiling/memory-usage-without-debugging2.md).  
  
> [!NOTE]
>  **Supporto allocatore personalizzato.** Il profiler della memoria nativo raccoglie dati relativi a eventi [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) di allocazione generati in fase di esecuzione.  Gli allocatori in CRT e Windows SDK sono stati annotati a livello di origine in modo che sia possibile acquisirne i dati di allocazione.  Nella scrittura degli allocatori, fare in modo che qualsiasi funzione che restituisce un puntatore alla memoria heap appena allocata possa essere decorata con [__declspec](/cpp/cpp/declspec)(allocator), come illustrato in questo esempio per myMalloc:  
>   
>  `__declspec(allocator) void* myMalloc(size_t size)` 

## <a name="collect-memory-usage-data"></a>Raccogliere i dati sull'utilizzo della memoria

1.  Aprire il progetto per cui si vuole eseguire il debug in Visual Studio e impostare un punto di interruzione nell'app in corrispondenza del punto in cui si vuole iniziare a esaminare l'utilizzo della memoria.

    Se è presente un'area in cui si sospetta un problema di memoria, impostare il primo punto di interruzione prima che si verifichi tale problema.

    > [!TIP]
    >  Poiché può essere difficile acquisire il profilo di memoria di un'operazione specifica quando l'app alloca e dealloca spesso la memoria, impostare punti di interruzione all'inizio e alla fine dell'operazione o eseguire i vari passaggi dell'operazione per trovare il punto esatto in cui l'utilizzo della memoria è cambiato. 

2.  Impostare un secondo punto di interruzione alla fine della funzione o dell'area di codice da analizzare o dopo un problema di utilizzo sospetto della memoria.
  
3.  La finestra **Strumenti di diagnostica** viene visualizzata automaticamente, a meno che non sia stata disattivata. Per visualizzare di nuovo la finestra, fare clic su **Debug/Windows/Mostra strumenti di diagnostica**.

4.  Scegliere **Utilizzo memoria** con l'impostazione **Seleziona strumenti** sulla barra degli strumenti.

     ![Mostra strumenti di diagnostica](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

5.  Fare clic su **Debug / Avvia debug** (o **Avvia** sulla barra degli strumenti o **F5**).

     Al termine del caricamento dell'applicazione viene visualizzato il riepilogo degli strumenti di diagnostica.

     ![Strumenti di diagnostica Scheda Riepilogo](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     > [!NOTE]
     >  Poiché la raccolta di dati può influire sulle prestazioni di debug delle app native o in modalità mista, gli snapshot di memoria sono disattivati per impostazione predefinita. Per abilitare gli snapshot in app native o in modalità mista, avviare una sessione di debug (tasto di scelta rapida: **F5**). Quando viene visualizzata la finestra **Strumenti di diagnostica**, scegliere la scheda Utilizzo memoria e quindi **Profilatura heap**.  
     >   
     >  ![Abilita snapshot](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
     >   
     >  Arrestare (tasto di scelta rapida: **MAIUSC + F5**) e riavviare il debug.  

6.  Per creare uno snapshot all'inizio della sessione di debug, scegliere **Crea snapshot** sulla barra degli strumenti di riepilogo **Utilizzo memoria**. Può essere utile impostare anche qui un punto di interruzione.

    ![Crea snapshot](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot") 
     
     > [!TIP]
     >  Per creare una linea di base per i confronti di memoria, si consiglia di creare uno snapshot all'inizio di una sessione di debug.  

6.  Eseguire lo scenario in cui viene raggiunto il primo punto di interruzione.

7.  Quando il debugger viene messo in pausa in corrispondenza del primo punto di interruzione, scegliere **Crea snapshot** sulla barra degli strumenti di riepilogo **Utilizzo memoria**.  

8.  Premere F5 per eseguire l'applicazione fino al secondo punto di interruzione.

9.  A questo punto, creare un altro snapshot.

     A questo punto, è possibile iniziare ad analizzare i dati.    
  
## <a name="analyze-memory-usage-data"></a>Analizzare i dati di utilizzo della memoria
Nelle righe della tabella di riepilogo Utilizzo memoria sono elencati gli snapshot creati durante la sessione di debug e sono disponibili collegamenti a visualizzazioni più dettagliate.

![Tabella di riepilogo della memoria](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Il nome delle colonne dipende dalla modalità di debug selezionata nelle proprietà del progetto: .NET, nativa o mista (nativa e .NET).  
  
-   Le colonne **Oggetti (diff)**e **Allocazioni (diff)** visualizzano il numero di oggetti nella memoria .NET e nativa quando è stato creato lo snapshot.  
  
-   La colonna **Dimensioni heap (diff)** visualizza il numero di byte negli heap nativi e .NET 

Quando si eseguono più snapshot, le celle della tabella di riepilogo includono la modifica del valore tra lo snapshot della riga e lo snapshot precedente.  

Per analizzare l'utilizzo della memoria, fare clic su uno dei collegamenti che consente di visualizzare un report dettagliato dell'utilizzo della memoria:  

-   Per visualizzare i dettagli della differenza tra lo snapshot corrente e quello precedente, scegliere il collegamento di modifica a sinistra della freccia (![Aumento nell'utilizzo della memoria](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento nell'utilizzo della memoria")). Una freccia rossa indica un aumento nell'utilizzo della memoria, mentre una freccia verde indica una riduzione.

    > [!TIP]
    >  Per identificare i problemi di memoria più rapidamente, i report diff vengono ordinati in base ai tipi di oggetto che sono aumentati maggiormente in termini di numero (fare clic sul collegamento di modifica nella colonna **Oggetti (diff)**) o di dimensioni complessive dell'heap (fare clic sul collegamento di modifica nella colonna **Dimensioni heap (diff)**).

-   Per visualizzare i dettagli relativi solo allo snapshot selezionato, fare clic sul collegamento non di modifica. 
  
 Il report verrà visualizzato in una finestra separata.   
  
### <a name="managed-types-reports"></a>Report di tipi gestiti  
 Scegliere il collegamento corrente di una cella **Oggetti (diff)** o **Allocazioni (diff)** nella tabella di riepilogo Utilizzo memoria.  
  
 ![Report di tipo gestito del debugger &#45; Percorsi della radice](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Il riquadro superiore mostra il numero e la dimensione dei tipi dello snapshot, inclusa la dimensione di tutti gli oggetti cui fa riferimento il tipo (**Dimensione inclusiva**).  
  
 L'albero **Percorsi della radice** del riquadro inferiore mostra gli oggetti che fanno riferimento al tipo selezionato nel riquadro superiore. Il Garbage Collector di .NET Framework pulisce la memoria per un oggetto solo quando è stato rilasciato l'ultimo tipo cui fa riferimento.  
  
 L'albero **Tipi a cui si fa riferimento** mostra i riferimenti mantenuti dal tipo selezionato nel riquadro superiore.  
  
 ![Visualizzazione del report di tipi di riferimento gestiti](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Per visualizzare le istanze di un tipo selezionato nel riquadro superiore, scegliere l'icona ![Istanza](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon").  
  
 ![Visualizzazione Istanze](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 La visualizzazione **Istanze** mostra le istanze dell'oggetto selezionato nello snapshot nel riquadro superiore. I riquadri Percorsi della radice e Tipi a cui si fa riferimento mostrano gli oggetti che fanno riferimento all'istanza selezionata e i tipi cui fa riferimento l'istanza selezionata. Quando il debugger viene interrotto nel punto in cui è stato creato lo snapshot, è possibile passare il mouse sulla cella Valore per visualizzare i valori dell'oggetto in una descrizione comando.  
  
### <a name="native-type-reports"></a>Report di tipo nativo  
 Scegliere il collegamento corrente di una cella **Allocazioni (diff)** o **Dimensioni heap (diff)** della tabella di riepilogo Utilizzo memoria della finestra **Strumenti di diagnostica** .  
  
 ![Visualizzazione di tipo nativo](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 La **Visualizzazione Tipi** mostra il numero e la dimensione dei tipi dello snapshot.  
  
-   Scegliere l'icona delle istanze (![Icona dell'istanza nella colonna Tipo di oggetto](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) di un tipo selezionato per visualizzare le informazioni sugli oggetti del tipo selezionato nello snapshot.  
  
     La visualizzazione **Istanze** mostra ogni istanza del tipo selezionato. La selezione di un'istanza consente di visualizzare lo stack di chiamate che ha comportato la creazione dell'istanza nel riquadro **Stack di chiamate allocazione** .  
  
     ![Visualizzazione Istanze](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")  
  
-   Scegliere **Visualizzazione stack** dall'elenco **Modalità di visualizzazione** per visualizzare lo stack di allocazione per il tipo selezionato.  
  
     ![Visualizzazione Stack](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Report di modifica (Diff)  
  
-   Scegliere il collegamento di modifica in una cella della tabella di riepilogo della scheda **Utilizzo memoria** nella finestra **Strumenti di diagnostica** .  
  
     ![Scegliere un report delle modifiche &#40;dif&#41;f](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
-   Scegliere uno snapshot dall'elenco **Confronta con** di un report gestito o nativo.  
  
     ![Scegliere uno snapshot dall'elenco Confronta con](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
 Il report di modifica aggiunge colonne (contrassegnate con **(Diff)**) al report di base che mostra la differenza tra il valore di snapshot di base e lo snapshot di confronto. Ecco un esempio di come potrebbe apparire un report delle differenze di visualizzazione del tipo nativo:  
  
 ![Visualizzazione differenze dei tipi nativi](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Blog e video  

|         |         |
|---------|---------|
|  ![icona della telecamera](../install/media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) sull'uso degli strumenti di diagnostica che illustra come analizzare l'uso della memoria e della CPU in Visual Studio 2017. |

 [Analizzare CPU e memoria in fase di debug](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Blog su Visual C++: profilatura della memoria in Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>Vedere anche
 [Profilatura in Visual Studio](../profiling/index.md)  
 [Tour delle funzionalità di profilatura](../profiling/profiling-feature-tour.md)