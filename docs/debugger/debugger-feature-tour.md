---
title: 'Il debugger di Visual Studio Tour delle funzionalità: | Documenti Microsoft'
description: Per una presentazione del debugger di Visual Studio
ms.custom: mvc
ms.date: 03/27/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb84fbfa4b8916b963f3f3cc35e044593c5a47e1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="quickstart-first-look-at-the-visual-studio-debugger"></a>Guida introduttiva: Analizzare innanzitutto il Debugger di Visual Studio

In questo argomento vengono presentate le funzionalità del debugger di Visual Studio. Se si desidera seguire la procedura per l'apertura di un'app in Visual Studio, è possibile farlo oppure è possibile seguire insieme a un'app di esempio usando il [Guida per principianti](../debugger/getting-started-with-the-debugger.md).

Le funzionalità descritte di seguito sono applicabili a c#, C++, Visual Basic, JavaScript e altri linguaggi supportati da Visual Studio (se non diversamente).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

Per eseguire il debug, è necessario avviare l'app con il debugger collegato al processo di app. F5 (**Debug > Avvia debug**) è il modo più comune a tale scopo. Tuttavia, ora si potrebbe non essere stato dei punti di interruzione per esaminare l'app il codice, pertanto verrà prima di eseguire e quindi avviare il debug.

Se è un file aperto nell'editor di codice, è possibile impostare un punto di interruzione facendo clic sul margine a sinistra di una riga di codice.

![Impostare un punto di interruzione](../debugger/media/dbg-tour-set-a-breakpoint.gif "impostare un punto di interruzione")

Premere F5 (**Debug > Avvia debug**) e il debugger viene eseguito il primo punto di interruzione viene rilevato. Se l'app non è ancora in esecuzione, F5 avvia il debugger e si ferma in corrispondenza del primo punto di interruzione.

I punti di interruzione sono una funzionalità utile quando si conosce la riga di codice o nella sezione di codice che si desidera esaminare in dettaglio.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Esplorare il codice nel debugger utilizzando i comandi di passaggio

Offriamo i tasti di scelta rapida per la maggior parte dei comandi poiché rendono più veloce di spostamento del codice dell'app. (Equivalente comandi quali i comandi di menu sono indicati tra parentesi).

Per avviare l'app con il debugger collegato, premere F11 (**Debug > Esegui istruzione**). F11 è il **Esegui istruzione** comando e fa avanzare il app esecuzione un'istruzione alla volta. Quando si avvia l'app con F11, il debugger interrompe la prima istruzione che viene eseguito.

![F11 Istruzione](../debugger/media/dbg-tour-f11.png "F11 Esegui istruzione")

La freccia gialla rappresenta l'istruzione in cui il debugger ha sospeso, che sospende l'esecuzione di app anche nello stesso punto (questa istruzione non è ancora eseguita).

F11 è un buon metodo per esaminare il flusso di esecuzione nella maggior parte dei dettagli. (Per spostare più rapidamente tramite codice, viene illustrata la altre opzioni nonché.) Per impostazione predefinita, il debugger passa al codice non utente (se si desidera visualizzare ulteriori dettagli, vedere [Just My Code](../debugger/just-my-code.md)).

>[!NOTE]
> Nel codice gestito, si noterà una finestra di dialogo che chiede se si desidera ricevere una notifica quando passa automaticamente le proprietà e operatori (comportamento predefinito). Se si desidera modificare l'impostazione in un secondo momento, disabilitare **Esegui istruzione/routine di proprietà e operatori** impostazione di **strumenti > Opzioni** menu sotto **debug**.

## <a name="step-over-code-to-skip-functions"></a>Esegui istruzione/routine di codice per ignorare le funzioni

Quando si utilizza una riga di codice che è una chiamata di funzione o un metodo, è possibile premere F10 (**Debug > Esegui istruzione/routine**) anziché F11.

F10 fa avanzare il debugger senza eseguire istruzioni di funzioni o metodi nel codice dell'app (il codice viene comunque eseguita). Premendo F10, è possibile ignorare il codice che non si è interessati. In questo modo, è possibile ottenere rapidamente al codice che si è più interessati.

## <a name="step-into-a-property"></a>Passaggio in una proprietà

Come accennato in precedenza, per impostazione predefinita, il debugger Ignora proprietà gestite e i campi, ma la **Esegui istruzione specifica** comando consente di eseguire l'override di questo comportamento.

Fare clic su una proprietà o campo e scegliere **Esegui istruzione specifica**, quindi scegliere una delle opzioni disponibili.

![Esegui istruzione specifici](../debugger/media/dbg-tour-step-into-specific.png "istruzione specifica")

In questo esempio, **Esegui istruzione specifica** ci Ottiene il codice per `Path.set`.

![Esegui istruzione specifici](../debugger/media/dbg-tour-step-into-specific-2.png "istruzione specifica")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Eseguire fino a un punto nel codice rapidamente usando il mouse

Quando nel debugger, passare il mouse su una riga di codice fino a quando il **eseguire fare clic su** pulsante (esecuzione qui) ![eseguire fare clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick") viene visualizzata a sinistra.

![Esegui fino al clic](../debugger/media/dbg-tour-run-to-click-2.png "eseguire fare clic su")

>  [!NOTE] 
> Il **eseguire fare clic su** pulsante (esecuzione qui) è una novità di [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Fare clic su di **eseguire fare clic su** pulsante (esecuzione qui). Il debugger avanza alla riga di codice in cui è stato selezionato.

Tramite questo pulsante è simile all'impostazione di un punto di interruzione temporanea. Questo comando è anche utile per operare su rapidamente all'interno di un'area visibile del codice dell'app. È possibile utilizzare **eseguire fare clic su** in qualsiasi file aperto.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Spostare il debugger dalla funzione corrente

In alcuni casi, si potrebbe voler continuare la sessione di debug ma fa avanzare il debugger attraverso la funzione corrente.

Premere MAIUSC + F11 (o **Debug > Esci da istruzione**).

Questo comando riprende l'esecuzione di app (e fa avanzare il debugger) fino alla restituzione della funzione corrente.

## <a name="run-to-cursor"></a>Esecuzione fino al cursore

Arrestare il debugger premendo il **Termina debug** pulsante rosso ![Termina debug](../debugger/media/dbg-tour-stop-debugging.png "Termina debug") o MAIUSC + F5.

Fare doppio clic su una riga di codice nell'app e scegli **Esegui fino al cursore**. Questo comando avvia il debug e imposta un punto di interruzione temporaneo nella riga di codice corrente.

![Esegui fino al cursore](../debugger/media/dbg-tour-run-to-cursor.png "Esegui fino al cursore")

Se sono stati impostati i punti di interruzione, il debugger sospende sul punto di interruzione prima che venga rilevato.

Premere F5 fino a raggiungere la riga di codice in cui è stata selezionata **Esegui fino al cursore**.

Questo comando è utile quando si modifica del codice e si desidera impostare un punto di interruzione temporaneo rapidamente e avviare il debugger.


> [!NOTE]
> È possibile utilizzare **Esegui fino al cursore** nel **Stack di chiamate** finestra durante il debug.

## <a name="restart-your-app-quickly"></a>Riavviare l'app rapidamente

Fare clic su di **riavviare** ![riavviare App](../debugger/media/dbg-tour-restart.png "riavviare App") pulsante nella barra degli strumenti Debug (**Ctrl + MAIUSC + F5**).

Quando si preme **riavviare**, consente di risparmiare tempo e l'arresto dell'app e riavviare il debugger. Il debugger sospende nel punto di interruzione prima che viene raggiunto mediante l'esecuzione di codice.

Se si desidera arrestare il debugger e tornare nell'editor di codice, è possibile premere l'arresto rosso ![Termina debug](../debugger/media/dbg-tour-stop-debugging.png "Termina debug") pulsante anziché **riavviare**.

## <a name="inspect-variables-with-data-tips"></a>Controllare le variabili con i suggerimenti dati

Ora che si conoscono le varie leggermente, si dispone di una buona opportunità per avviare controllando lo stato dell'app (variabili) con il debugger. Funzionalità che consentono di controllare le variabili sono riportate alcune delle funzionalità più utili del debugger e sono disponibili diversi modi per eseguire l'operazione. Spesso, quando si tenta di eseguire il debug di un problema, si sta tentando di scoprire se le variabili vengono archiviati i valori che si prevede di disporre di uno stato particolare app.

Durante la pausa nel debugger, passare il mouse su un oggetto con il mouse e viene visualizzato il valore della proprietà predefinito (in questo esempio, il nome del file `market 031.jpg` è il valore della proprietà predefinito).

![Visualizzare un suggerimento dati](../debugger/media/dbg-tour-data-tips.gif "visualizzare un suggerimento dati")

Espandere l'oggetto per visualizzare tutte le relative proprietà (ad esempio il `FullPath` proprietà in questo esempio).

Spesso, durante il debug, si desidera un modo rapido per verificare i valori delle proprietà per gli oggetti, e i suggerimenti dati sono un ottimo modo per farlo.

> [!TIP]
> In più lingue, è possibile modificare codice all'interno di una sessione di debug. Per altre informazioni, vedere [modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Controllare le variabili con le finestre variabili locali e Auto

Durante il debug, esaminare il **Auto** finestra nella parte inferiore dell'editor di codice.

![Finestra Auto](../debugger/media/dbg-tour-autos-window.png "auto (finestra)")

Nel **Auto** è visualizzare variabili lungo con il relativo valore corrente e dei relativi tipi. Il **Auto** finestra Visualizza tutte le variabili utilizzate nella riga corrente o nella riga precedente (In C++, la finestra Visualizza le variabili in tre righe di codice precedenti. Vedere la documentazione per il comportamento specifico del linguaggio).

> [!NOTE]
> In JavaScript, il **variabili locali** finestra è supportata ma non il **Auto** finestra.

Successivamente, esaminare il **variabili locali** finestra. Il **variabili locali** finestra Visualizza le variabili attualmente nell'ambito.

![Finestra variabili locali](../debugger/media/dbg-tour-locals-window.png "finestra variabili locali")

In questo esempio, il `this` oggetto e l'oggetto `f` nell'ambito. Per altre informazioni, vedere [esaminare le variabili nelle finestre variabili locali e Auto](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

È possibile utilizzare un **espressioni di controllo** finestra per specificare una variabile (o un'espressione) che si desidera tenere sotto controllo.

Durante il debug, fare doppio clic su un oggetto e scegliere **Aggiungi espressione di controllo**.

![Finestra Espressioni di controllo](../debugger/media/dbg-tour-watch-window.png "finestra Espressioni di controllo")

In questo esempio, è impostato su un'espressione di controllo di `File` oggetto ed è possibile visualizzarne il valore cambia quando sposta tramite il debugger. A differenza di altre finestre delle variabili, il **espressioni di controllo** windows Mostra sempre le variabili che sta controllando (è disattivati quando dall'ambito).

Per altre informazioni, vedere [impostare un'espressione di controllo utilizzando le espressioni di controllo e le finestre di controllo immediato](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

Fare clic su di **Stack di chiamate** finestra durante il debug, per impostazione predefinita è aperto nel riquadro inferiore destro.

![Esaminare lo Stack di chiamate](../debugger/media/dbg-tour-call-stack.png "esaminare lo stack di chiamate")

Il **Stack di chiamate** finestra Mostra l'ordine in cui sono chiamate i metodi e funzioni. La riga superiore viene illustrata la funzione corrente (il `Update` metodo in questo esempio). La seconda riga mostra che `Update` è stato chiamato dal `Path.set` e così via. Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

> [!NOTE]
> Il **Stack di chiamate** finestra è simile alla prospettiva di Debug in un IDE come Eclipse.

È possibile fare doppio clic su una riga di codice per passare a esaminare il codice sorgente e che viene modificato anche l'ambito corrente in esame dal debugger. Questo non fa avanzare il debugger.

È inoltre possibile utilizzare i menu di scelta rapida dal **Stack di chiamate** finestra per eseguire altre operazioni. Ad esempio, è possibile inserire punti di interruzione in funzioni specifiche, riavviare l'app utilizzando **Esegui fino al cursore**e per passare a esaminare il codice sorgente. Vedere [procedura: esaminare lo Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a>Esaminare l'eccezione

Quando l'app genera un'eccezione, il debugger passerà alla riga di codice che ha generato l'eccezione.
     
![Supporto eccezioni](../debugger/media/dbg-tour-exception-helper.png "supporto eccezioni")

In questo esempio, il **supporto eccezioni** Mostra un `System.Argument` eccezione e un messaggio di errore indicante che il percorso non è un modulo valido. In tal caso, sappiamo che si è verificato l'errore su un argomento di metodo o funzione.

In questo esempio, il `DirectoryInfo` chiamata dato l'errore archiviata in una stringa vuota il `value` variabile.

L'Helper di eccezione è un'ottima funzionalità che consentono di eseguire il debug degli errori. È anche possibile eseguire operazioni come visualizzazione dettagli dell'errore e aggiungere un'espressione di controllo il supporto di eccezioni. In alternativa, se necessario, è possibile modificare le condizioni per generare l'eccezione specifica.

>  [!NOTE] 
> L'Helper eccezioni sostituisce le informazioni sulle eccezioni in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Espandere il **impostazioni eccezioni** nodo per visualizzare ulteriori opzioni gestire questo tipo di eccezione, ma è necessario modificare alcun valore per questa presentazione.

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Debug di applicazioni ASP.NET in tempo reale in Azure App Service

il **Debugger Snapshot** un'istantanea delle applicazioni in produzione quando viene eseguito codice che si è interessati. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

![Avviare il debugger snapshot](../debugger/media/snapshot-launch.png "avviare il debugger di snapshot")

Raccolta di snapshot è disponibile per le applicazioni ASP.NET in esecuzione in Azure App Service. Applicazioni ASP.NET devono essere in esecuzione su .NET Framework 4.6.1 o versioni successive, e le applicazioni ASP.NET di base devono essere in esecuzione su .NET Core 2.0 o versione successiva in Windows.

Per ulteriori informazioni, vedere [Debug in tempo reale delle App ASP.NET utilizzando il Debugger Snapshot](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Visualizzare gli snapshot con IntelliTrace. passaggio-back (Visual Studio Enterprise)

**Passaggio di IntelliTrace-back** automaticamente un'istantanea dell'applicazione in ogni punto di interruzione e debugger evento di passaggio. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

È possibile esplorare e visualizzare gli snapshot tramite i pulsanti **Vai indietro** e **Vai avanti** sulla barra degli strumenti di Debug. Questi pulsanti consentono di spostarsi tra gli eventi visualizzati nella scheda **Eventi** della finestra **Strumenti di diagnostica**.

![Passo indietro e Avanti pulsanti](../debugger/media/intellitrace-step-back-icons-description.png  "pulsanti con le versioni precedenti di passaggio e l'inoltro")  

Per altre informazioni, vedere la pagina [Visualizzare gli snapshot con la funzionalità per tornare indietro di IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md).

## <a name="more-features-to-look-at"></a>Più funzionalità da esaminare

-   [Suggerimenti e trucchi del debugger](../debugger/debugger-tips-and-tricks.md) informazioni su come aumentare la produttività con il debugger.

-   [Modifica e continuazione](../debugger/edit-and-continue.md) per un sottoinsieme di lingue (c#, C++, Visual Basic), la funzionalità Modifica e continuazione consente di modificare il codice all'interno di una sessione di debug.

-   [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md) viene descritto come eseguire il debug delle applicazioni multithreading. 

-   [Debug remoto](../debugger/remote-debugging.md) viene descritto come eseguire il debug delle applicazioni in esecuzione in altri computer o dispositivi. 
  
-   [IntelliTrace](../debugger/intellitrace.md) descrive la funzionalità di IntelliTrace in Visual Studio Enterprise. È possibile utilizzare il record e traccia cronologia di esecuzione del codice.

-   [Utilizzo della rete](../profiling/network-usage.md) descrive uno strumento di profilatura che è possibile utilizzare per eseguire il debug di servizi web e altre risorse di rete in Windows le app UWP (Universal). Utilizzare lo strumento per esaminare i payload.

-   [Debug Interface Access SDK](../debugger/debug-interface-access/debug-interface-access-sdk.md) descrive Microsoft Debug Interface Access Software Development Kit (DIA SDK). Il DIA SDK fornisce l'accesso alle informazioni di debug archiviate nei file di database di programma (PDB) generati dagli strumenti di post-compilazione di Microsoft.  

## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)
