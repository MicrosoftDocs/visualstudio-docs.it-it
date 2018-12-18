---
title: Informazioni su come eseguire il debug con Visual Studio | Documenti Microsoft
ms.custom: H1HackMay2017
ms.date: 10/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords: debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a09e0c54f1d7f0e49f08ddf65afbeb030a7087f1
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="learn-to-debug-using-visual-studio"></a>Viene illustrato come eseguire il debug con Visual Studio

In questo argomento vengono presentate le funzionalità del debugger di Visual Studio in una procedura dettagliata. Se si desidera una visualizzazione di livello superiore delle funzionalità di debug, vedere [Debugger funzionalità presentazione](../debugger/debugger-feature-tour.md).

È possibile leggere sia lungo per visualizzare le funzionalità del debugger o è possibile scaricare l'esempio completo utilizzato nella presentazione di funzionalità e seguire i passaggi manualmente. Per scaricare l'esempio e seguire la procedura, passare a [Photo Viewer Demo](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![icona della telecamera](../install/media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) debug che illustra una procedura simile. |

Benché l'app demo è c#, le funzionalità sono applicabili a C++, Visual Basic, JavaScript e altri linguaggi supportati da Visual Studio (se non diversamente).

## <a name="start-the-debugger"></a>Avviare il debugger.

1. Per seguire la procedura seguente procedura in Visual Studio, scaricare l'esempio [in questa pagina](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > È necessario installare Visual Studio con il carico di lavoro di sviluppo Desktop .NET per eseguire l'app che viene usata la demo.

2. Decomprimere il progetto.

3. Aprire Visual Studio e selezionare il **File > aprire** menu comando, quindi scegliere **progetto/soluzione**e quindi aprire la cartella in cui è stato scaricato il progetto.

     ![Aprire il progetto di esempio](../debugger/media/dbg-tour-open-project.png "Apri progetto")

3. Aprire il Visualizzatore WPF Photo Demo > c# cartella, scegliere il file photoapp.sln e selezionare **aprire**.

     Il progetto verrà aperto in Visual Studio. Esplora soluzioni nel riquadro destro mostra tutti i file di progetto.

    ![File di Esplora soluzioni](../debugger/media/dbg-tour-solution-explorer.png "Esplora soluzioni")

4. Premere F5 (**Debug > Avvia debug** o **Avvia debug** pulsante ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") nella barra degli strumenti di Debug).

     ![App Visualizzatore foto](../debugger/media/dbg-tour-wpf-app.png "App Visualizzatore di foto")

     F5 avvia l'app con il debugger al processo dell'app, ma destra è non aggiunto i punti di interruzione o fatto nulla per esaminare il codice. Pertanto l'app viene semplicemente caricata e verranno visualizzate le immagini foto.

     In questa esercitazione, si sarà un quadro più vicino all'app usando il debugger e ottenere esaminerà il debugger funzionalità.

5. Arrestare il debugger premendo l'arresto rosso ![Termina debug](../debugger/media/dbg-tour-stop-debugging.png "Termina debug") pulsante.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

Per eseguire il debug, è necessario avviare l'app con il debugger collegato al processo di app.

1. Nel `MainWindow` costruttore di MainWindow.xaml.cs, impostare un punto di interruzione facendo clic sul margine sinistro della prima riga di codice.

     ![Impostare un punto di interruzione](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

6. Premere F5 o **Avvia debug** pulsante, l'avvio dell'applicazione, e il debugger viene eseguito dalla riga di codice in cui è stato impostato il punto di interruzione.

    La freccia gialla rappresenta l'istruzione in cui il debugger ha sospeso, che sospende l'esecuzione di app anche nello stesso punto (questa istruzione non è ancora eseguita).

    F5 continua l'esecuzione dell'applicazione per il punto di interruzione successivo. (Se l'app non è ancora in esecuzione, F5 avvia il debugger e si ferma in corrispondenza del primo punto di interruzione).

    I punti di interruzione sono una funzionalità utile quando si conosce la riga di codice o nella sezione di codice che si desidera esaminare in dettaglio.

## <a name="restart-your-app-quickly"></a>Riavviare l'app rapidamente

1. Fare clic su di **riavviare** ![riavviare App](../debugger/media/dbg-tour-restart.png "RestartApp") pulsante nella barra degli strumenti Debug (Ctrl + MAIUSC + F5).

    Quando si preme **riavviare**, consente di risparmiare tempo e l'arresto dell'app e riavviare il debugger. Il debugger sospende nel punto di interruzione prima che viene raggiunto mediante l'esecuzione di codice.

    Il debugger si arresta nuovamente nel punto di interruzione è impostato, nel `MainWindow` costruttore.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Esplorare il codice nel debugger utilizzando i comandi di passaggio

In genere, è utilizzare tasti di scelta rapida in questo caso, perché è un buon metodo per ottenere veloce nell'esecuzione dell'app nel debugger (comandi equivalenti, ad esempio menu comandi sono indicati tra parentesi).

1. Premere F11 (**Debug > Esegui istruzione**) due volte per anticipare l'esecuzione dell'app per il `InitializeComponent()` (funzione).

     ![Premere F11 per Esegui istruzione codice](../debugger/media/dbg-tour-f11.png "F11 Esegui istruzione")

     F11 è il **Esegui istruzione** comando e fa avanzare il app esecuzione un'istruzione alla volta. F11 è un buon metodo per esaminare il flusso di esecuzione nella maggior parte dei dettagli. (Per spostare più rapidamente tramite codice, viene illustrata la alcune altre opzioni inoltre.) Per impostazione predefinita, il debugger passa al codice non utente (se si desidera visualizzare ulteriori dettagli, vedere [Just My Code](../debugger/just-my-code.md)).

     >[!NOTE]
     > Nel codice gestito, si noterà una finestra di dialogo che chiede se si desidera ricevere una notifica quando passa automaticamente le proprietà e operatori (comportamento predefinito). Se si desidera modificare l'impostazione in un secondo momento, disabilitare **Esegui istruzione/routine di proprietà e operatori** impostazione di **strumenti > Opzioni** menu sotto **debug**.

2. Premere F10 (**Debug > Esegui istruzione/routine**) più volte fino a quando il debugger si interrompe alla prima riga di codice il `OnApplicationStartup` gestore dell'evento.

     ![Premere F10 per Esegui istruzione/routine codice](../debugger/media/dbg-tour-f10-step-over.png "F10 Esegui istruzione/routine")

     F10 fa avanzare il debugger senza eseguire istruzioni di funzioni o metodi nel codice dell'app (il codice viene comunque eseguita). Premendo F10 sul `InitializeComponent` chiamata al metodo (anziché F11), viene ignorato il codice di implementazione per `InitializeComponent` (quali ad esempio se ci non stiamo interessano ora).

## <a name="step-into-a-property"></a>Passaggio in una proprietà

1. Con il debugger è in pausa su questa riga di codice:

    ````
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Fare doppio clic sulla riga di codice e scegliere **Esegui istruzione specifica**, quindi **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Utilizzare la funzionalità specifica](../debugger/media/dbg-tour-step-into-specific.png "Esegui istruzione specifica")

    Come accennato in precedenza, per impostazione predefinita, il debugger Ignora proprietà gestite e i campi, ma la **Esegui istruzione specifica** comando consente di eseguire l'override di questo comportamento. Per il momento, si vuole osservare cosa accade quando il `Path.set` esecuzioni setter di proprietà. **Esegui istruzione specifica** Ottiene per la `Path.set` codice qui.

     ![risultato dell'istruzione specifica](../debugger/media/dbg-tour-step-into-specific-2.png "Esegui istruzione specifica")

     Il `Update` metodo in questo codice sembra che potrebbe essere interessante, pertanto consente di utilizzano il debugger per esaminare il codice di chiusura.

5. Passare il mouse su di `Update` metodo fino a quando il verde **eseguire fare clic su** pulsante ![eseguire fare clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick") viene visualizzata a sinistra.

     ![Utilizzare l'esecuzione di fare clic su funzionalità](../debugger/media/dbg-tour-run-to-click-2.png "eseguire fare clic su")

    >  [!NOTE] 
    > Il **eseguire fare clic su** pulsante è stato introdotto in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Se non viene visualizzato il pulsante freccia verde, utilizzare F11 in questo esempio per far avanzare il debugger.

6. Fare clic su di **eseguire fare clic su** pulsante ![eseguire fare clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Tramite questo pulsante è simile all'impostazione di un punto di interruzione temporanea. **Eseguire fino a fare clic su** è utile per operare su rapidamente all'interno di un'area visibile del codice dell'app (è possibile fare clic in qualsiasi file aperto).

    Il debugger avanza fino il `Update` implementazione del metodo.

7. Premere F11 per eseguire il `Update` metodo.

     ![Risultato dell'esecuzione di istruzioni il metodo Update](../debugger/media/dbg-tour-update-method.png "Step in Update (metodo)")

    In questo caso, si trova codice che sembra interessante; l'app stia ottenendo tutti i file che si trovano in una directory specifica e quindi creare un oggetto foto per ogni file *. jpg. Questo codice produce una buona opportunità per avviare controllando lo stato dell'app (variabili) con il debugger. Che verranno eseguite nelle sezioni successive di questa esercitazione.

    Funzionalità che consentono di controllare le variabili sono una delle funzionalità più utili del debugger e sono disponibili diversi modi per eseguire l'operazione. Spesso, quando si tenta di eseguire il debug di un problema, si sta tentando di scoprire se le variabili vengono archiviati i valori che si prevede di disporre di un determinato momento.

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

- Durante la sospensione nel `Update` (metodo), fare clic su di **Stack di chiamate** finestra, per impostazione predefinita è aperto nel riquadro inferiore destro.

     ![Esaminare lo stack di chiamate](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

    Il **Stack di chiamate** finestra Mostra l'ordine in cui sono chiamate i metodi e funzioni. La riga superiore viene illustrata la funzione corrente (il `Update` metodo nell'applicazione di presentazione). La seconda riga mostra che `Update` è stato chiamato dal `Path.set` e così via.

    >  [!NOTE]
    > Il **Stack di chiamate** finestra è simile alla prospettiva di Debug in un IDE come Eclipse.

    Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

    È possibile fare doppio clic su una riga di codice per passare a esaminare il codice sorgente e che viene modificato anche l'ambito corrente in esame dal debugger. Questa azione non fa avanzare il debugger.

    È inoltre possibile utilizzare i menu di scelta rapida dal **Stack di chiamate** finestra per eseguire altre operazioni. Ad esempio, è possibile inserire punti di interruzione in funzioni specificate, spostare il debugger usando **Esegui fino al cursore**e passare a esaminare il codice sorgente. Per ulteriori informazioni, vedere [procedura: esaminare lo Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Esci da istruzione

Si supponga di avere esaminando il `Update` metodo Data.cs e si desidera ottenere dalla funzione ma di rimanere nel debugger. È possibile farlo usando il **Esci** comando.

1. Premere MAIUSC + F11 (o **Debug > Esci da istruzione**).

     Questo comando riprende l'esecuzione di app (e fa avanzare il debugger) fino alla restituzione della funzione corrente.

     Dovrebbe essere nuovamente il `Update` chiamata al metodo in Data.cs.

2. Premere MAIUSC + F11 nuovamente e il debugger di eseguire il backup si lo stack di chiamate per il `OnApplicationStartup` gestore dell'evento.

## <a name="run-to-cursor"></a>Esecuzione fino al cursore

1. Scegliere il **Termina debug** pulsante rosso ![Termina debug](../debugger/media/dbg-tour-stop-debugging.png "Termina debug") o MAIUSC + F5.

2. Nel `Update` metodo Data.cs, fare doppio clic su di `Add` chiamate di metodo e scegliere **Esegui fino al cursore**. Questo comando avvia il debug e imposta un punto di interruzione temporaneo nella riga di codice corrente.

     ![Utilizzare l'esecuzione alla funzionalità di cursore](../debugger/media/dbg-tour-run-to-cursor.png "Esegui fino al cursore")

    Deve essere interrotta nel punto di interruzione `MainWindow` (dal momento che è il primo punto di interruzione è impostato).

3. Premere F5 per spostare il `Add` metodo in cui è stata selezionata **Esegui fino al cursore**.

    Questo comando è utile quando si modifica del codice e si desidera impostare un punto di interruzione temporaneo rapidamente e avviare il debugger.

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

1. Con il debugger sospesa sul `Add` chiamata al metodo, utilizzare il mouse per trascinare la freccia gialla (il puntatore di esecuzione) a sinistra e spostare la freccia gialla alto di una riga per il `foreach` ciclo.

     ![Spostare il puntatore di esecuzione](../debugger/media/dbg-tour-move-the-execution-pointer.gif "spostare il puntatore di esecuzione")

    Se si modifica il flusso di esecuzione, è possibile eseguire operazioni quali percorsi di esecuzione diverso codice di test o eseguire di nuovo codice senza dover riavviare il debugger.

2. A questo punto, premere F5.

    È possibile visualizzare le immagini aggiunte nella finestra dell'applicazione. Poiché si sta eseguendo nuovamente codice il `foreach` ciclo, alcune delle immagini sono state aggiunte due volte.
    
    > [!WARNING]
    > Spesso è necessario prestare attenzione con questa funzionalità, e viene visualizzato un avviso nella descrizione comando. È possibile visualizzare altri avvisi, troppo. Spostare il puntatore non è possibile ripristinare l'applicazione su uno stato precedente di app.

## <a name="inspect-variables-with-data-tips"></a>Controllare le variabili con i suggerimenti dati

1. Aprire Data.cs nell'app Demo Visualizzatore foto, fare doppio clic su di `private void Update` dichiarazione di funzione e scegliere **Esegui fino al cursore** (arrestare l'applicazione prima di tutto se è già in esecuzione).

    Sospende l'app con il debugger collegato. Ciò consente di esaminare il relativo stato.

2. Passare il mouse su di `Add` metodo chiamare e fare clic su di **eseguire fare clic su** pulsante ![eseguire fare clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. A questo punto, passare il mouse sopra l'oggetto File (`f`) e viene visualizzato il valore della proprietà predefinito, il nome del file `market 031.jpg`.

     ![Visualizzare un suggerimento dati](../debugger/media/dbg-tour-data-tips.gif "consente di visualizzare un suggerimento dati")

4. Espandere l'oggetto per visualizzare tutte le relative proprietà, ad esempio il `FullPath` proprietà.

    Spesso, durante il debug, si desidera un modo rapido per verificare i valori delle proprietà per gli oggetti, e i suggerimenti dati sono un ottimo modo per farlo.

    > [!TIP]
    > In più lingue, è possibile modificare il codice all'interno di una sessione del debugger se si trova qualcosa che si desidera modificare. Per altre informazioni, vedere [modifica e continuazione](../debugger/edit-and-continue.md). Per utilizzare tale funzionalità in questa app, tuttavia, è prima di tutto dovrebbe aggiornare la versione dell'applicazione di .NET Framework.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Controllare le variabili con le finestre variabili locali e Auto

1. Esaminare il **Auto** finestra nella parte inferiore dell'editor di codice.

     ![Controllare le variabili nella finestra Auto](../debugger/media/dbg-tour-autos-window.png "auto (finestra)")

    Nel **Auto** finestra, vedrai variabili e il relativo valore corrente. Il **Auto** finestra Visualizza tutte le variabili utilizzate nella riga corrente o nella riga precedente (In C++, la finestra Visualizza le variabili in tre righe di codice precedenti. Vedere la documentazione per il comportamento specifico del linguaggio).

    > [!NOTE]
    > In JavaScript, il **variabili locali** finestra è supportata ma non il **Auto** finestra.

2. Successivamente, esaminare il **variabili locali** finestra.

    Il **variabili locali** finestra Visualizza le variabili nell'ambito corrente.

    ![Controllare le variabili nella finestra variabili locali](../debugger/media/dbg-tour-locals-window.png "finestra variabili locali")

    Attualmente, il `this` oggetto e l'oggetto File (`f`) si trovano nell'ambito corrente. Per altre informazioni, vedere [esaminare le variabili nelle finestre variabili locali e Auto](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

1. Nella finestra dell'editor di codice principale, fare doppio clic su oggetto File (`f`) e scegliere **Aggiungi espressione di controllo**.

    È possibile utilizzare un **espressioni di controllo** finestra per specificare una variabile (o un'espressione) che si desidera tenere sotto controllo.

    È ora possibile impostare in un'espressione di controllo di `File` oggetto ed è possibile visualizzarne il valore cambia quando sposta tramite il debugger. A differenza di altre finestre delle variabili, il **espressioni di controllo** finestra Visualizza sempre le variabili che sta controllando (è disattivati quando dall'ambito).

2. Nel `Add` (metodo), fare clic su verde ![eseguire fare clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick") nuovamente clic sul pulsante (o premere F11 più volte) per passare il `foreach` ciclo.

    ![Impostare un'espressione di controllo in una variabile](../debugger/media/dbg-tour-watch-window.png "finestra Espressioni di controllo")

    È possibile visualizzare l'immagine prima richiedere di essere aggiunti alla finestra principale di esecuzione dell'app di esempio, ma questo accade in un thread di un'app, quindi le immagini potrebbero non essere visibile ancora.

    Per altre informazioni, vedere [impostare un'espressione di controllo utilizzando le espressioni di controllo e le finestre di controllo immediato](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Esaminare l'eccezione

1. Nella finestra dell'applicazione in esecuzione, eliminare il testo di **percorso** casella di input e selezionare il **modifica** pulsante.

     ![Un'eccezione generata](../debugger/media/dbg-tour-cause-an-exception.png "generare un'eccezione")

     L'applicazione genera un'eccezione e il debugger consente di passare alla riga di codice che ha generato l'eccezione.
     
     ![Supporto eccezioni](../debugger/media/dbg-tour-exception-helper.png "supporto eccezioni")

     In questo caso, il **supporto eccezioni** Mostra un `System.ArgumentException` e un messaggio di errore indicante che il percorso non è un modulo valido. In tal caso, sappiamo che si è verificato l'errore su un argomento di metodo o funzione.

     In questo esempio, il `DirectoryInfo` chiamata dato l'errore archiviata in una stringa vuota il `value` variabile. (Mouse `value` per visualizzare una stringa vuota.)

     L'Helper di eccezione è un'ottima funzionalità che consentono di eseguire il debug degli errori. È anche possibile eseguire operazioni come visualizzazione dettagli dell'errore e aggiungere un'espressione di controllo il supporto di eccezioni. In alternativa, se necessario, è possibile modificare le condizioni per generare l'eccezione specifica.

    >  [!NOTE] 
    > L'Helper eccezioni sostituisce le informazioni sulle eccezioni in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Espandere il **impostazioni eccezioni** nodo per visualizzare ulteriori opzioni gestire questo tipo di eccezione, ma è necessario modificare alcun valore per questa presentazione.

3. Premere F5 per continuare l'app.

Per ulteriori informazioni sulle funzionalità del debugger, vedere [Debugger suggerimenti e consigli](../debugger/debugger-tips-and-tricks.md).

## <a name="see-also"></a>Vedere anche

[Debug in Visual Studio](../debugger/index.md)  
[Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
