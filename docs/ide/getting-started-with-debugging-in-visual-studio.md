---
title: Introduzione al debug in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e858d24a37fec49468981b44d450212ba2fa3654
ms.sourcegitcommit: 3285243d6c0521266053340fe06505885d12178b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/09/2018
---
# <a name="get-started-with-debugging-in-visual-studio"></a>Introduzione al debug in Visual Studio
Visual Studio offre un set integrato di strumenti efficaci per il debug e la compilazione dei progetti. Questo argomento spiega come iniziare a usare il set di base delle funzionalità dell'interfaccia utente di debug.  

Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

## <a name="my-code-doesnt-work-help-me-visual-studio"></a>Il codice non funziona. Come risolvere il problema?  
 Dopo aver acquisito familiarità con l'editor e aver creato il codice, è possibile iniziare il debug del codice. In Visual Studio, come nella maggior parte degli IDE, il debug viene eseguito in due fasi: la compilazione del codice per rilevare e risolvere gli errori relativi al progetto e al compilatore e l'esecuzione del codice nell'ambiente per rilevare e risolvere gli errori dinamici e di run-time.  

### <a name="build-your-code"></a>Compilare il codice  
 Sono disponibili due tipi di base per la configurazione della build: **Debug** e **Release**. La prima configurazione produce un file eseguibile più lento e di dimensioni maggiori che offre un'esperienza di debug del runtime interattiva più completa, ma che non deve essere mai distribuito. La seconda configurazione compila un file eseguibile più veloce e ottimizzato, adatto alla distribuzione (almeno dal punto di vista del compilatore). La configurazione predefinita della build è **Debug**.

Il modo più semplice per compilare il progetto è premere **F7**, ma è anche possibile avviare la compilazione selezionando **Compila -> Compila soluzione** dal menu principale.  

 ![Selezione del menu del progetto di compilazione di Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png "Vs_ide_gs_debug_build_menu_item")  

 È possibile osservare il processo di compilazione nella finestra di stato **Output** nella parte inferiore dell'interfaccia utente di Visual Studio, dove vengono visualizzati gli eventuali errori, avvisi e operazioni di compilazione. In caso di errori (o se vengono rilevati avvisi di livello superiore a quello configurato), la compilazione non riuscirà. È possibile fare clic su errori e avvisi per passare alla riga in cui si sono verificati. Ricompilare il progetto premendo di nuovo **F7**, per ricompilare solo i file con errori, o **CTRL+ALT+F7**, per una ricompilazione pulita e completa.  

 Nella finestra dei risultati sotto l'editor vengono visualizzate due finestre a schede della compilazione: la finestra **Output** che contiene l'output del compilatore non elaborato (compresi i messaggi di errore) e la finestra **Elenco errori** che visualizza un elenco ordinabile e filtrabile di tutti gli errori e gli avvisi.  

 Se l'operazione viene completata correttamente, nella finestra **Output** vengono visualizzati risultati simili ai seguenti.  

 ![Output di compilazione di Visual Studio con esito positivo](../ide/media/vs_ide_gs_debug_success_build.PNG "vs_ide_gs_debug_success_build")  

### <a name="review-the-error-list"></a>Rivedere l'elenco errori  
 A meno che non siano state apportate modifiche al codice compilato correttamente in precedenza, è probabile si verifichi un errore. Se non si ha familiarità con la codifica, gli errori potrebbero essere numerosi. Gli errori possono essere talvolta elementari, ad esempio un semplice errore di sintassi o un nome di variabile non corretto, oppure difficili da comprendere, in cui l'unico aiuto è un codice non facile da decifrare. Per una visualizzazione più chiara dei problemi, passare alla parte inferiore della finestra di compilazione **Output** e scegliere la scheda **Elenco errori**. Si apre una visualizzazione più organizzata degli errori e degli avvisi relativi al progetto in cui vengono fornite anche alcune opzioni aggiuntive.  

 ![Elenco errori in Output di Visual Studio](../ide/media/vs_ide_gs_debug_bad_build_error_list.PNG "Vs_ide_gs_debug_bad_build_error_list")  

 Fare clic sulla riga di errore nella finestra **Elenco errori** per passare alla riga in cui si è verificato l'errore. In alternativa, attivare i numeri di riga facendo clic sulla barra **Avvio veloce** in alto a destra, digitando "numeri di riga" al suo interno e premendo INVIO. Questo è il modo più rapido per passare alla voce della finestra **Opzioni** in cui è possibile attivare i numeri di riga. Per risparmiare tempo, è consigliabile imparare a usare la barra **Avvio veloce**.  

 ![Editor di Visual Studio con numeri di riga](../ide/media/vs_ide_gs_debug_line_numbers.png "Vs_ide_gs_debug_line_numbers")  

 ![Opzione numeri di riga di Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png "Vs_ide_gs_debug_options_line_numbers")  

 Per passare rapidamente al numero di riga in cui si è verificato l'errore, premere **CTRL+G**.  

 L'errore viene segnalato da una sottolineatura rossa "a zigzag". Per altri dettagli, passare il mouse sull'errore. Correggere il problema per farlo scomparire. La correzione, però, potrebbe causare un nuovo errore. Questo fenomeno viene chiamato "regressione".  

 ![Passare il mouse sull'errore in Visual Studio](../ide/media/vs_ide_gs_debug_error_hover1.png "Vs_ide_gs_debug_error_hover1")  

 Scorrere l'elenco degli errori e risolvere tutti gli errori nel codice.  

 ![Finestra di debug degli errori in Visual Studio ](../ide/media/vs_ide_gs_debug_error_list.PNG "Vs_ide_gs_debug_error_list")  

### <a name="review-errors-in-detail"></a>Rivedere gli errori in dettaglio  
 Molti errori possono essere poco comprensibili per l'utente poiché sono stati espressi con un linguaggio da compilatori. In questi casi sono necessarie informazioni aggiuntive. Dalla finestra **Elenco errori** è possibile eseguire una ricerca automatica in Bing per ottenere altre informazioni sull'errore, o sull'avviso, facendo clic con il pulsante destro del mouse sulla riga corrispondente e scegliendo **Mostra guida errore** dal menu di scelta rapida.  

 ![Ricerca elenco errori con Bing in Visual Studio](../ide/media/vs_ide_gs_debug_error_list_error_help.png "Vs_ide_gs_debug_error_list_error_help")  

 Viene avviata una scheda all'interno di Visual Studio che ospita i risultati della ricerca in Bing relativa al codice e al testo dell'errore. I risultati provengono da diverse origini in Internet, quindi è probabile che non tutti siano utili.  

 In alternativa, è possibile fare clic sul valore del codice di errore con collegamento ipertestuale nella colonna **Codice** dell'**Elenco errori**. Viene avviata una ricerca in Bing solo per lo specifico codice di errore.  

### <a name="use-light-bulbs-to-fix-or-refactor-code"></a>Usare le lampadine per correggere o effettuare il refactoring del codice  
 Le lampadine sono una nuova funzionalità di Visual Studio che consente di effettuare il refactoring del codice inline. Consentono di risolvere con la massima semplicità gli avvisi più comuni in modo rapido ed efficace. Per accedere a questa nuova funzionalità, fare clic con il pulsante destro del mouse sulla sottolineatura a zigzag di un avviso o premere **CTRL+**. mentre si passa il mouse sulla sottolineatura, e selezionare **Azioni rapide**.  

 ![Opzioni rapide con lampadine in Visual Studio](../ide/media/vs_ide_gs_debug_light_bulb1.png "Vs_ide_gs_debug_light_bulb1")  

 Verrà visualizzato un elenco di possibili correzioni o refactoring che è possibile applicare alla riga di codice.  

 ![Anteprima delle lampadine in Visual Studio](../ide/media/vs_ide_gs_debug_light_bulb_preview_changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")  

 Le lampadine possono essere usate in tutti i casi in cui gli analizzatori di codice individuano la possibilità di correggere, eseguire il refactoring o migliorare il codice. Fare clic su una qualsiasi riga di codice, fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida e selezionare **Azioni rapide** oppure, per aumentare l'efficienza, premere **CTRL+**. Se sono disponibili opzioni di refactoring o di miglioramento, verranno visualizzate. In caso contrario, verrà visualizzato il messaggio `No quick options available here` nel riquadro nell'angolo inferiore sinistro dell'IDE.  

 ![Testo lampadina nessuna opzione in Visual Studio](../ide/media/vs_ide_gs_debug_light_bulb_no_options.PNG "Vs_ide_gs_debug_light_bulb_no_options")  

 Con l'esperienza si apprenderà a usare rapidamente i tasti di direzione e **CTRL+**. per controllare se sia possibile eseguire il refactoring con Azioni rapide e per pulire il codice.  

 Per altre informazioni sulle lampadine, vedere [Perform quick actions with light bulbs](../ide/perform-quick-actions-with-light-bulbs.md) (Eseguire azioni rapide con le lampadine).  

### <a name="debug-your-running-code"></a>Eseguire il debug del codice in esecuzione  
 Dopo aver compilato correttamente il codice e aver eseguito qualche attività di pulizia, eseguire il codice premendo **F5** o selezionando **Debug -> Avvia debug**. L'applicazione verrà avviata in un ambiente di debug in modo che sia possibile osservarne il comportamento in modo dettagliato. L'IDE di Visual Studio viene modificato mentre l'applicazione è in esecuzione. La finestra **Output** viene sostituita da due nuove finestre a schede (nella configurazione predefinita della finestra): **Auto/Variabili locali/Espressione di controllo** e **Stack di chiamate/Punti di interruzione/Impostazioni eccezione/Output**. In queste finestre sono presenti più schede che consentono di esaminare e valutare le variabili, i thread, gli stack di chiamate e vari altri comportamenti dell'app durante l'esecuzione.  

 ![Finestre Auto e Stack di chiamate in Visual Studio](../ide/media/vs_ide_gs_debug_autos_and_call_stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")  

 È possibile arrestare l'app premendo **MAIUSC+F5** o facendo clic sul pulsante **Arresta**. In alternativa, è possibile chiudere semplicemente la finestra principale dell'app o la finestra di dialogo della riga di comando.  

 Se il codice è stato eseguito senza errori ed esattamente come previsto, complimenti! In caso di blocco, arresto anomalo o risultati imprevisti, è necessario individuare l'origine dei problemi e correggere i bug.  

### <a name="set-simple-breakpoints"></a>Impostare punti di interruzione semplici  
 I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice. NON è necessario ricompilare un progetto dopo l'impostazione e la rimozione dei punti di interruzione.  

 Impostare un punto di interruzione facendo clic sul margine più esterno della riga in cui si vuole inserire l'interruzione oppure premere **F9** per impostare un punto di interruzione nella riga di codice corrente. Quando si esegue il codice, questo verrà sospeso oppure *interrotto* prima dell'esecuzione delle istruzioni per la riga di codice specificata.  

 ![Punto di interruzione in Visual Studio](../ide/media/vs_ide_gs_debug_breakpoint1.png "Vs_ide_gs_debug_breakpoint1")   

 Di seguito sono riportati alcuni usi comuni dei punti di interruzione:  

1.  Per limitare l'origine di un arresto anomalo o di blocco, inserirli all'interno e intorno al codice della chiamata al metodo che si ritiene causi l'errore. Durante l'esecuzione del codice nel debugger, rimuovere e reimpostare i punti di interruzione fino a individuare la riga di codice interessata.  Vedere la sezione successiva per informazioni su come eseguire il codice nel debugger.

2.  Quando si introduce un nuovo codice, impostare un punto di interruzione all'inizio del codice ed eseguire il codice per verificare che funzioni come previsto.

3.  Se è stato implementato un comportamento complesso, impostare punti di interruzione per il codice algoritmico affinché sia possibile esaminare i valori delle variabili e i dati quando il programma si interrompe.  

4.  Se si scrive codice C o C++, usare i punti di interruzione per arrestare il codice affinché sia possibile esaminare i valori di indirizzo (cercare NULL) e conteggi riferimenti durante il debug degli errori correlati alla memoria.  

 Per altre informazioni sull'uso dei punti di interruzione, vedere [Uso di punti di interruzione](../debugger/using-breakpoints.md).  

### <a name="inspect-your-code-at-run-time"></a>Esaminare il codice in fase di esecuzione  
 Quando il codice in esecuzione incontra un punto di interruzione e viene sospeso, la riga di codice contrassegnata in giallo, ovvero l'istruzione corrente, non è ancora stata eseguita. A questo punto, è possibile eseguire l'istruzione corrente ed esaminare i valori modificati. È possibile usare diversi comandi di *esecuzione* per eseguire il codice nel debugger. Se il codice contrassegnato è una chiamata a un metodo, è possibile eseguire le istruzioni premendo **F11**. È anche possibile *eseguire l'istruzione/la routine* per la riga di codice premendo **F10**. Per informazioni su altri comandi e informazioni dettagliate su come esaminare il codice, leggere [Spostarsi nel codice con il debugger](../debugger/navigating-through-code-with-the-debugger.md).

 ![Esame del valore di run&#45;time in Visual Studio](../ide/media/vs_ide_gs_debug_hit_breakpoint.PNG "vs_ide_gs_debug_inspect_value")

 Nell'illustrazione precedente, è possibile spostarsi in un'istruzione con il debugger premendo **F10** o **F11**. In questo caso non si verifica una chiamata al metodo e pertanto il risultato dei due comandi è lo stesso.

 Quando il debugger viene sospeso, è possibile esaminare le variabili e gli stack di chiamate per individuare il problema. I valori sono compresi negli intervalli previsti? L'ordine con cui si stanno eseguendo le chiamate è corretto?  

 ![Esame del valore di run&#45;time in Visual Studio](../ide/media/vs_ide_gs_debug_inspect_value.PNG "vs_ide_gs_debug_inspect_value")  

 Passare il mouse su una variabile per visualizzare i valori e i riferimenti attualmente contenuti. Se viene visualizzato un valore non previsto, è probabile che ci sia un bug nelle righe di codice precedenti o chiamate.  Per i dettagli, [leggere altre informazioni ](../debugger/getting-started-with-the-debugger.md) sull'uso del debugger.

 Visual Studio visualizza anche la finestra Strumenti di diagnostica, in cui è possibile osservare l'utilizzo della memoria e della CPU dell'app nel corso del tempo. Durante lo sviluppo dell'app, è possibile usare questi strumenti per individuare l'utilizzo intenso della CPU imprevisto o l'allocazione della memoria. Usare contemporaneamente anche la finestra **Espressione di controllo** e i punti di interruzione per determinare la causa di questo utilizzo intenso imprevisto o del mancato rilascio delle risorse.  Per altre informazioni, vedere [Panoramica delle funzionalità di profilatura](../profiling/profiling-feature-tour.md).

### <a name="run-unit-tests"></a>Eseguire unit test  
 Gli unit test sono il primo elemento di difesa da bug nel codice perché, se eseguiti correttamente, testano una singola "unità" di codice, in genere una singola funzione. Anche eseguire il debug di una singola unità piuttosto che dell'intero programma risulta più semplice. Visual Studio installa i framework degli unit test di Microsoft sia per il codice gestito e che per quello nativo. Usare un framework di testing unità per creare unit test, eseguirli e riportare i risultati dei test. Eseguire nuovamente gli unit test quando si apportano modifiche per verificare che il codice funzioni ancora correttamente. Quando si usa Visual Studio Enterprise, è possibile eseguire automaticamente i test dopo ogni compilazione.  

 Per iniziare, vedere [Generate unit tests for your code with IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) (Generare unit test per il codice con IntelliTest).  

 Per altre informazioni sugli unit test in Visual Studio e su come usarli per creare codice di qualità migliore, vedere [Unit Test Basics](../test/unit-test-basics.md) (Nozioni di base sugli unit test).  

### <a name="perform-static-code-analysis"></a>Eseguire l'analisi statica del codice  
 L'analisi statica del codice consente di controllare automaticamente il codice alla ricerca di problemi frequenti che possono causare errori di runtime o problemi nella gestione del codice. È consigliabile eseguire questa analisi dopo aver rimosso gli errori più semplici che impediscono la compilazione e di dedicare del tempo alla risoluzione degli eventuali avvisi restituiti. In questo modo si prevengono altri problemi in futuro e si apprendono alcune tecniche relative allo stile del codice.  

 Per avviare l'analisi statica del codice, premere **ALT+F11** o selezionare **Analizza -> Esegui analisi del codice sulla soluzione** dal menu principale. Se la quantità di codice è elevata, l'operazione potrebbe richiedere del tempo.  

 ![Voce di menu per analisi del codice in Visual Studio](../ide/media/vs_ide_gs_debug_run_code_analysis.png "Vs_ide_gs_debug_run_code_analysis")  

 Eventuali avvisi nuovi o aggiornati verranno visualizzati nella scheda **Elenco errori** nella parte inferiore dell'IDE. Fare clic sugli avvisi per aprirli.  

 ![Elenco di errori con avvisi in Visual Studio](../ide/media/vs_ide_gs_debug_code_analysis_warning_error_list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")  

 Gli avvisi verranno identificati con una sottolineatura giallo-verde brillante a zigzag, anziché rossa. Passare il mouse su di essi per ulteriori dettagli e fare clic con il pulsante destro del mouse per visualizzare un menu di scelta rapida in cui vengono fornite funzionalità di supporto per le correzioni o opzioni di refactoring.  

 ![Passare con il mouse sugli avvisi di analisi del codice in Visual Studio](../ide/media/vs_ide_gs_debug_code_analysis_warning_hover.png "vs_ide_gs_debug_code_analysis_warning_hover")  

## <a name="see-also"></a>Vedere anche  
 [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)  
 [Altre informazioni sull'uso del debugger](../debugger/getting-started-with-the-debugger.md)
