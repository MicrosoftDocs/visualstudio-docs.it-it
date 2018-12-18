---
title: Suggerimenti e consigli nel Debugger di Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 06/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dacce06dc59724b7f8feba8f84d2b781ba56ed9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Informazioni sui suggerimenti e consigli per il Debugger in Visual Studio

Leggere questo argomento per informazioni su alcuni suggerimenti e consigli per il debugger di Visual Studio. Per esaminare le funzionalità di base del debugger, vedere [Debugger funzionalità presentazione](../debugger/debugger-feature-tour.md). In questo argomento viene illustrata l'alcune aree che non sono incluse nella presentazione di funzionalità.

## <a name="pin-data-tips"></a>Suggerimenti dati pin

Se si passa spesso sui suggerimenti dati durante il debug, si desidera aggiungere il suggerimento dati per la variabile per disporre di accesso rapido. La variabile rimane bloccata anche dopo il riavvio. Per bloccare il suggerimento dati, fare clic sull'icona della puntina durante il passaggio del mouse su di esso. È possibile aggiungere più variabili.

![Aggiunta di un suggerimento dati](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Modificare il codice e continuare il debug (in c#, VB, C++)

Nella maggior parte dei linguaggi supportati da Visual Studio, è possibile modificare il codice all'interno di una sessione di debug e continuare il debug. Per utilizzare questa funzionalità, fare clic nel codice con il cursore durante la sospensione nel debugger, apportare modifiche e premere **F5**, **F10**, o **F11** per continuare il debug.

![Modifica e continuazione debug](../debugger/media/dbg-tips-edit-and-continue.gif "ignorato")

Per ulteriori informazioni sull'uso della funzionalità e limitazioni di funzionalità, vedere [modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Debug dei problemi che sono difficili da riprodurre

Se risulta difficile o lunghi ricreare un determinato stato nell'applicazione, prendere in considerazione se consentono l'utilizzo di un punto di interruzione condizionale. È possibile utilizzare [punti di interruzione condizionali](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) e filtrare i punti di interruzione per evitare l'interruzione nel codice dell'app fino a quando l'app passa allo stato desiderato (ad esempio uno stato in cui una variabile è archiviati i dati non validi). È possibile impostare le condizioni tramite espressioni, filtri, conteggio e così via.

#### <a name="to-create-a-conditional-breakpoint"></a>Per creare un punto di interruzione condizionale

1. Fare doppio clic sull'icona di un punto di interruzione (sfera rossa) e scegliere **condizioni**.

2. Nel **impostazioni punto di interruzione** finestra, digitare un'espressione.

    ![Punto di interruzione condizionale](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Se è interessati a un altro tipo di condizione, selezionare **filtro** anziché **espressione condizionale** nel **impostazioni punto di interruzione** la finestra di dialogo e quindi osservando la suggerimenti di filtro.

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

Con il debugger sospesa su una riga di codice, utilizzare il mouse per trascinare il puntatore freccia gialla a sinistra. Spostare il puntatore freccia gialla in un altro punto nel percorso di esecuzione di codice. E quindi utilizzare F5 o un comando del passaggio per continuare l'esecuzione dell'applicazione.

![Spostare il puntatore di esecuzione](../debugger/media/dbg-tour-move-the-execution-pointer.gif "spostare il puntatore di esecuzione")

Se si modifica il flusso di esecuzione, è possibile eseguire operazioni quali percorsi di esecuzione diverso codice di test o eseguire di nuovo codice senza dover riavviare il debugger.

> [!WARNING]
> Spesso è necessario prestare attenzione con questa funzionalità, e viene visualizzato un avviso nella descrizione comando. È possibile visualizzare altri avvisi, troppo. Spostare il puntatore non è possibile ripristinare l'app in uno stato applicazione precedente.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Tenere traccia di un oggetto out-of-scope (c#, Visual Basic)

È facile visualizzare variabili tramite finestre del debugger, ad esempio il **espressioni di controllo** finestra. Tuttavia, quando una variabile esce dall'ambito nel **espressioni di controllo** finestra, è possibile notare che è inattivo. In alcuni scenari di app, il valore di una variabile può variare anche quando la variabile esula dall'ambito, e si desidera osservare come strettamente (ad esempio, una variabile venga raccolto nel garbage collector). È possibile monitorare la variabile tramite la creazione di un ID di oggetto nella **espressioni di controllo** finestra.

#### <a name="to-create-an-object-id"></a>Per creare un ID di oggetto

1.  Impostare un punto di interruzione in prossimità di una variabile che si desidera tenere traccia.

2.  Avviare il debugger (**F5**) e interrompere nel punto di interruzione.

3. Trovare la variabile nel **variabili locali** finestra (**Debug > Windows > variabili locali**), la variabile e scegliere **Crea ID oggetto**.

    ![Creare un ID oggetto](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  Nella finestra **$** verrà visualizzato il simbolo **Variabili locali** . Questa variabile è l'ID oggetto.
  
5.  La variabile oggetto con ID di mouse e scegliere **Aggiungi espressione di controllo**.

Per ulteriori informazioni, vedere [creare un ID oggetto](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Visualizzare i valori restituiti per le funzioni

Per visualizzare i valori restituiti per le funzioni, esaminare le funzioni che vengono visualizzati nel **Auto** finestra mentre eseguono le istruzioni del codice. Per visualizzare il valore restituito per una funzione, assicurarsi che la funzione di cui si è interessati è già stata eseguita (premere **F10** volte se sono arrestati sulla chiamata di funzione). Se la finestra viene chiusa, utilizzare **Debug > Windows > Auto** per aprire la **Auto** finestra.

![Finestra Auto](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Inoltre, è possibile immettere funzioni il **immediato** consente di visualizzare i valori restituiti. (Aprirlo utilizzando **Debug > Windows > immediato**.)

![Finestra di controllo immediato](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

È inoltre possibile utilizzare [pseudo variabili](../debugger/pseudovariables.md) nel **espressioni di controllo** e **immediato** finestra, ad esempio `$ReturnValue`.

## <a name="string_visualizer"></a>Controllare le stringhe in un visualizzatore

Quando si utilizzano stringhe, può essere utile visualizzare l'intera stringa di formato. Per visualizzare un testo normale, la stringa JSON, XML o HTML, fare clic sull'icona di lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore") durante il passaggio del mouse su una variabile che contiene un valore stringa.

![Aprire un visualizzatore di stringhe](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualizzatore di stringhe consentono di verificare la disponibilità di una stringa in formato non corretto, a seconda del tipo di stringa. Ad esempio, un valore vuoto **valore** campo indica la stringa non è riconosciuta per il tipo del visualizzatore. Per ulteriori informazioni, vedere [dialogo Visualizzatore stringhe](../debugger/string-visualizer-dialog-box.md).

![Visualizzatore di stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Per alcuni altri tipi, ad esempio oggetti WPF visualizzati nelle finestre del debugger, è anche possibile aprire i visualizzatori.

## <a name="break-into-code-on-handled-exceptions"></a>Inserire un'interruzione nel codice di eccezioni gestite

Il debugger interrompe nel codice su eccezioni non gestite. Eccezioni gestite, tuttavia, (ad esempio le eccezioni che si verificano all'interno di un `try/catch` blocco) può anche essere un'origine dei bug e si potrebbe voler conoscere quando si verificano. È possibile configurare il debugger per inserire un'interruzione nel codice per le eccezioni gestite tramite la configurazione di opzioni di **impostazioni eccezioni** la finestra di dialogo. Aprire questa finestra di dialogo scegliendo **Debug > Windows > Impostazioni eccezioni**.

Il **impostazioni eccezioni** la finestra di dialogo consente di indicare al debugger di inserire un'interruzione nel codice per eccezioni specifiche. Nell'illustrazione seguente, il debugger si interrompe nel codice ogni volta che un `System.NullReferenceException` si verifica. Per ulteriori informazioni, vedere [la gestione delle eccezioni](../debugger/managing-exceptions-with-the-debugger.md).

![Finestra di dialogo Impostazioni eccezione](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Eseguire il debug di race condition e deadlock

Se è necessario eseguire il debug di tipi di problemi comuni per applicazioni multithreading, è spesso utile per visualizzare la posizione dei thread durante il debug. È possibile farlo con facilità utilizzando la **Mostra thread nell'origine** pulsante.

#### <a name="to-show-threads-in-your-source-code"></a>Per mostrare i thread nel codice sorgente

1.  Durante il debug, fare clic su di **Mostra thread nell'origine** pulsante ![Mostra thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") nel **Debug** barra degli strumenti.
  
2.  All'estrema sinistra della finestra, In questa riga, viene visualizzato un *marcatore del thread* icona ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") che due fili. Il marcatore del thread indica l'interruzione di un thread in questa posizione.

    Si noti che un marcatore del thread potrebbe essere parzialmente nascosta da un punto di interruzione.
  
3.  Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati. in cui è indicato il nome e il numero ID di ciascun thread interrotto.

    È inoltre possibile visualizzare il percorso del thread di [finestra Stack in parallelo](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Esaminare i payload per servizi web e alle risorse di rete (UWP)

Nelle App UWP, è possibile analizzare le operazioni di rete eseguite utilizzando il `Windows.Web.Http` API. È possibile utilizzare questo strumento per eseguire il debug di servizi web e le risorse di rete. Per utilizzare lo strumento, selezionare **Debug > Profiler delle prestazioni**. Selezionare **rete**, quindi scegliere **avviare**. Nell'applicazione seguire lo scenario che usa `Windows.Web.Http` e quindi scegliere **Arresta raccolta** per generare il report.

![Utilizzo di strumento di analisi di rete](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Selezionare un'operazione nella visualizzazione di riepilogo per visualizzare altri dettagli.

![Informazioni dettagliate nello strumento utilizzo rete](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Per altre informazioni, vedere [Utilizzo della rete](../profiling/network-usage.md).

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app"></a>Ottenere una maggiore familiarità con la modalità con cui il debugger si connette all'App

Per connettere l'App in esecuzione, il debugger carica il file di simboli (PDB) generati per la stessa build dell'app a cui che si sta tentando di eseguire il debug. In alcuni scenari, conoscenza dei file di simboli possono essere utile. È possibile esaminare la modalità di caricamento dei file di simboli tramite Visual Studio il **moduli** finestra.

Aprire il **moduli** finestra durante il debug selezionando **Debug > Windows > moduli**. Il **moduli** finestra può indicare quali il debugger viene considerato codice utente, i moduli o [ *My Code*](../debugger/just-my-code.md)e il simbolo di stato per il modulo di caricamento. Nella maggior parte degli scenari, il debugger individua automaticamente i file di simboli per codice utente, ma se si desidera eseguire l'istruzione (o eseguire il debug) codice .NET framework, codice di sistema o il codice di libreria di terze parti, sono necessari ulteriori passaggi per ottenere i file di simboli corretto.

![Visualizzare informazioni sui simboli nella finestra moduli](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

È possibile caricare le informazioni sui simboli direttamente il **moduli** finestra facendo clic e scegliendo **Carica simboli**.

In alcuni casi, gli sviluppatori di app rilasciato App senza i corrispondente file di simboli (per ridurre il footprint), ma occorre tenere una copia del simbolo corrispondente file per la compilazione in modo che possono eseguire il debug una versione rilasciata in un secondo momento.

Per sapere come il debugger classifica codice come codice utente, vedere [Just My Code](../debugger/just-my-code.md). Per ulteriori informazioni sui file di simboli, vedere [specificare simboli (PDB) e i file di origine nel debugger di Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Altre informazioni

Per altri suggerimenti e consigli e informazioni più dettagliate, vedere questi post di blog:

- [7 attacchi noti inferiore per il debug in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 nascoste in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Vedere anche
[Tasti di scelta rapida](../ide/tips-and-tricks-for-visual-studio.md)
