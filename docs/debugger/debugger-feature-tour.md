---
title: Presentazione del debugger
description: Introduzione al debug di applicazioni con il debugger di Visual Studio
ms.custom: ''
ms.date: 04/08/2019
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5bfa190f3bbc2a4f8b34d42d62b0ccc9b293674a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873132"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Presentazione del debugger di Visual Studio

Questo argomento presenta gli strumenti debugger disponibili in Visual Studio. Nel contesto di Visual Studio il *debug di un'app* implica in genere l'esecuzione dell'applicazione con il debugger collegato, ovvero in modalità debugger. Durante il debug, il debugger offre diversi modi per vedere le operazioni eseguite dal codice durante l'esecuzione. È possibile eseguire il codice un'istruzione alla volta ed esaminare i valori archiviati nelle variabili. è possibile impostare gli orologi sulle variabili per vedere quando cambiano i valori, è possibile esaminare il percorso di esecuzione del codice, et al. Se è la prima volta che si tenta di eseguire il debug del codice, è consigliabile leggere il [debug per principianti assoluti prima di passare a](../debugger/debugging-absolute-beginners.md) questo argomento.

Le funzionalità qui descritte sono applicabili a C#, C++, Visual Basic, JavaScript e ad altri linguaggi supportati da Visual Studio (se non diversamente specificato).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

Per eseguire il debug è necessario avviare l'app con il debugger collegato al processo dell'app. **F5** (**Debug > Avvia debug**) è il modo più comune per eseguire questa operazione. Tuttavia, è possibile che non sia ancora stato impostato alcun punto di interruzione per esaminare il codice dell'app, quindi si eseguirà prima questa operazione e quindi si avvierà il debug. I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

Se si ha un file aperto nell'editor del codice, è possibile impostare un punto di interruzione facendo clic sul margine a sinistra di una riga di codice.

![Imposta un punto di interruzione](../debugger/media/dbg-tour-set-a-breakpoint.gif "Imposta punto di interruzione")

Premere **F5** (**debug > Avvia debug**) o il pulsante **Avvia debug** ![Avvia](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") debug sulla barra degli strumenti debug e il debugger viene eseguito fino al primo punto di interruzione rilevato. Se l'app non è ancora in esecuzione, F5 avvia il debugger e lo arresta in corrispondenza del primo punto di interruzione.

I punti di interruzione sono una funzionalità utile quando si conosce la riga di codice o la sezione di codice che si vuole esaminare nel dettaglio.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> Esplorare il codice nel debugger usando i comandi Step

Per la maggior parte dei comandi è possibile usare tasti di scelta rapida per esplorare velocemente il codice dell'app. I comandi equivalenti, ad esempio i comandi di menu, sono visualizzati tra parentesi.

Per avviare l'app con il debugger collegato, premere **F11** (**Debug > Esegui istruzione**). F11 corrisponde al comando **Esegui istruzione** e consente di eseguire l'app un'istruzione alla volta. Quando si avvia l'app con F11, il debugger si interrompe alla prima istruzione che viene eseguita.

![Esegui istruzione F11](../debugger/media/dbg-tour-f11.png "Esegui istruzione F11")

La freccia gialla rappresenta l'istruzione in corrispondenza della quale il debugger si è interrotto e il punto in cui anche l'esecuzione dell'app viene sospesa (l'istruzione non è ancora stata eseguita).

F11 è un buon metodo per esaminare il flusso di esecuzione nel dettaglio. (Per spostarsi più rapidamente tramite codice, vengono mostrate anche altre opzioni). Per impostazione predefinita, il debugger ignora il codice non utente (se si desiderano maggiori dettagli, vedere [Just My Code](../debugger/just-my-code.md)).

>[!NOTE]
> Nel codice gestito verrà visualizzata una finestra di dialogo in cui si chiede all'utente se vuole ricevere una notifica quando vengono eseguite automaticamente istruzioni di proprietà e operatori (comportamento predefinito). Per modificare l'impostazione in un secondo momento, disabilitare l'impostazione **Esegui istruzione/routine di proprietà e operatori** nel menu **Strumenti > Opzioni** in **Debug**.

## <a name="step-over-code-to-skip-functions"></a>Eseguire le istruzione del codice per ignorare le funzioni

Quando si è in una riga di codice che è una chiamata di funzione o metodo si può premere **F10** (**Debug > Esegui istruzione/routine**) anziché F11.

F10 fa avanzare il debugger senza eseguire le istruzioni di funzioni o metodi presenti nel codice dell'app (il codice viene comunque eseguito). Premendo F10, è possibile ignorare il codice a cui non si è interessati. In questo modo si può raggiungere rapidamente il codice a cui si è più interessati.

## <a name="step-into-a-property"></a>Eseguire le istruzioni di una proprietà

Come accennato in precedenza, per impostazione predefinita il debugger ignora proprietà e campi gestiti, ma il comando **Esegui istruzione specifica** consente di eseguire l'override di questo comportamento.

Fare clic con il pulsante destro del mouse su una proprietà o un campo e scegliere **Esegui istruzione specifica**, quindi scegliere una delle opzioni disponibili.

![Screenshot del debugger di Visual Studio con una riga di codice evidenziata. Esegui istruzione specifica è selezionato nel menu di scelta rapida e il metodo Path. set è selezionato.](../debugger/media/dbg-tour-step-into-specific.png)

In questo esempio **Esegui istruzione specifica** si interrompe in corrispondenza del codice per `Path.set`.

![Screenshot del debugger di Visual Studio che mostra il codice per Path. set. Le parentesi graffe che racchiudono la funzione set sono evidenziate in giallo.](../debugger/media/dbg-tour-step-into-specific-2.png)

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Raggiungere rapidamente un punto del codice usando il mouse

Nel debugger passare il puntatore del mouse su una riga di codice fino a quando non **si fa clic** sul pulsante Esegui esecuzione fino a qui, ![ screenshot del pulsante Esegui fino al clic dal debugger di Visual Studio. Il pulsante indica che l'esecuzione deve essere eseguita fino alla riga in cui si trova il pulsante.](../debugger/media/dbg-tour-run-to-click.png) viene visualizzata a sinistra.

![Screenshot del debugger di Visual Studio che mostra il pulsante Esegui fino al clic visualizzato a sinistra di una chiamata alla funzione Update.](../debugger/media/dbg-tour-run-to-click-2.png)

> [!NOTE]
> Il pulsante **Esegui fino alla riga selezionata** (Continua l'esecuzione fino a qui) è disponibile a partire da [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Fare clic sul pulsante per l'**esecuzione fino alla riga selezionata** (Continua l'esecuzione fino a qui). Il debugger avanza fino alla riga di codice in cui si è fatto clic.

L'uso di questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. Questo comando è utile anche per spostarsi rapidamente all'interno di un'area visibile del codice dell'app. È possibile usare il pulsante per l'**esecuzione fino alla riga selezionata** in qualsiasi file aperto.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Far avanzare il debugger all'esterno della funzione corrente

In alcuni casi può essere necessario continuare la sessione di debug facendo tuttavia avanzare il debugger all'esterno della funzione corrente.

Premere **MAIUSC + F11** oppure **Debug > Esci da istruzione/routine**.

Questo comando riprende l'esecuzione dell'app e fa avanzare il debugger fino alla fine della funzione corrente.

## <a name="run-to-cursor"></a>Esecuzione fino al cursore

Quando si modifica il codice (anziché sospendere il debugger), fare clic con il pulsante destro del mouse su una riga di codice nell'app e scegliere **Esegui fino al cursore** oppure premere **CTRL** per **F10**. Questo comando avvia il debug e imposta un punto di interruzione temporaneo nella riga di codice corrente.

![Esegui fino al cursore](../debugger/media/dbg-tour-run-to-cursor.png "Esegui fino al cursore")

Se sono stati impostati punti di interruzione, il debugger viene sospeso in corrispondenza del primo punto di interruzione.

Premere **F5** fino a raggiungere la riga di codice in cui è stato selezionato **Esegui fino al cursore**.

Questo comando è utile quando si modifica il codice e si vuole impostare rapidamente un punto di interruzione temporaneo e avviare allo stesso tempo il debugger.

> [!NOTE]
> È possibile usare **Esegui fino al cursore** nella finestra **Stack di chiamate** durante il debug.

## <a name="restart-your-app-quickly"></a>Riavviare rapidamente l'app

Fare clic sul pulsante **Riavvia** ![app riavvia](../debugger/media/dbg-tour-restart.png "Riavvia l'app") sulla barra degli strumenti Debug oppure premere **CTRL + MAIUSC + F5**.

Il pulsante **Riavvia** consente di risparmiare tempo rispetto all'arresto dell'app e al riavvio del debugger. Il debugger viene messo in pausa in corrispondenza del primo punto di interruzione raggiunto eseguendo il codice.

Se si desidera arrestare il debugger e tornare all'editor di codice, è possibile premere il pulsante di arresto del ![debug](../debugger/media/dbg-tour-stop-debugging.png "Debug") rosso anziché **Riavvia**.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Modificare il codice e continuare il debug (C#, VB, C++, XAML)

Nella maggior parte dei linguaggi supportati da Visual Studio, è possibile modificare il codice nel corso di una sessione di debug e continuare il debug. Per usare questa funzionalità, fare clic sul codice con il cursore mentre è in pausa nel debugger, apportare modifiche e premere **F5**, **F10** o **F11** per continuare il debug.

![Debug di modifica e continuazione](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Per ulteriori informazioni sull'utilizzo della funzionalità e sulle limitazioni delle funzionalità, vedere [modifica e continuazione](../debugger/edit-and-continue.md).

Per modificare il codice XAML durante una sessione di debug, vedere [scrivere ed eseguire il debug di codice XAML in esecuzione con il ricaricamento a caldo di XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="inspect-variables-with-data-tips"></a>Esaminare le variabili con i suggerimenti dati

Dopo aver acquisito una conoscenza generale si può iniziare a esaminare lo stato dell'app (variabili) con il debugger. Le funzionalità che consentono di esaminare le variabili sono tra le più utili del debugger e sono disponibili diversi modi per eseguire questa operazione. Quando si prova a eseguire il debug di un problema, spesso si tenta di determinare se le variabili includono i valori previsti in un particolare stato dell'app.

Con il debugger in pausa, passare il puntatore del mouse su un oggetto per visualizzarne il valore della proprietà predefinita (in questo esempio il nome di file `market 031.jpg` è il valore della proprietà predefinita).

![Visualizzare un suggerimento dati](../debugger/media/dbg-tour-data-tips.gif "Visualizzare un suggerimento dati")

Espandere l'oggetto per visualizzare tutte le proprietà, ad esempio la proprietà `FullPath` in questo esempio.

Spesso durante il debug è utile avere a disposizione un modo rapido per controllare i valori delle proprietà negli oggetti e i suggerimenti dati sono un ottimo strumento per eseguire questa operazione.

> [!TIP]
> Nella maggior parte dei linguaggi supportati è possibile modificare il codice durante una sessione di debug. Per altre informazioni, vedere [Modificare il codice e continuare il debug](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Esaminare le variabili con le finestre Auto e Variabili locali

Durante il debug, osservare la finestra **Auto** nella parte inferiore dell'editor del codice.

![Finestra auto](../debugger/media/dbg-tour-autos-window.png "Auto (finestra)")

Nella finestra **Auto** vengono visualizzate le variabili con il relativo valore corrente e il tipo. La finestra **Auto** contiene tutte le variabili usate nella riga corrente o nella riga precedente (in C++ la finestra contiene le variabili nelle tre righe di codice precedenti. Vedere la documentazione per il comportamento specifico del linguaggio).

> [!NOTE]
> In JavaScript è supportata la finestra **Variabili locali** ma non la finestra **Auto**.

Osservare quindi la finestra **Variabili locali**. La finestra **Variabili locali** contiene le variabili presenti attualmente nell'ambito.

![finestra Variabili locali](../debugger/media/dbg-tour-locals-window.png "Finestra Variabili locali")

In questo esempio l'oggetto `this` e l'oggetto `f` rientrano nell'ambito. Per altre informazioni, vedere [Inspect Variables in the Autos and Locals Windows](../debugger/autos-and-locals-windows.md) (Esaminare le variabili nelle finestre Auto e Variabili locali).

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

È possibile usare una finestra **Espressione di controllo** per specificare una variabile (o un'espressione) che si vuole controllare.

Durante il debug, fare clic con il pulsante destro del mouse su un oggetto e scegliere **Aggiungi espressione di controllo**.

![finestra Espressioni di controllo](../debugger/media/dbg-tour-watch-window.png "Finestra Espressioni di controllo")

In questo esempio è stata impostata un'espressione di controllo sull'oggetto `f` ed è possibile vederne le modifiche al valore mentre ci si sposta nel debugger. A differenza di altre finestre delle variabili, la finestra **Espressione di controllo** visualizza sempre le variabili controllate (che appaiono disattivate quando non rientrano nell'ambito).

Per altre informazioni, vedere [Set a Watch using the Watch and QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md) (Impostare un'espressione di controllo usando le finestre Espressione di controllo e Controllo immediato)

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

Durante il debug, fare clic sulla finestra **Stack di chiamate** aperta, per impostazione predefinita, nel riquadro inferiore destro.

![Esaminare lo stack di chiamate](../debugger/media/dbg-tour-call-stack.png "Esaminare lo stack di chiamate")

La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. La prima riga visualizza la funzione corrente (il metodo `Update` in questo esempio). La seconda riga indica che `Update` è stato chiamato dalla proprietà `Path.set` e così via. Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

> [!NOTE]
> La finestra **Stack di chiamate** è simile alla prospettiva di debug di alcuni IDE come Eclipse.

È possibile fare doppio clic su una riga di codice per visualizzare il codice sorgente e modificare anche l'ambito corrente controllato dal debugger. Ciò non determina l'avanzamento del debugger.

È anche possibile usare i menu di scelta rapida nella finestra **Stack di chiamate** per eseguire altre operazioni. Ad esempio, è possibile inserire punti di interruzione in funzioni specifiche, riavviare l'app usando **Esegui fino al cursore** e passare a esaminare il codice sorgente. Vedere [Procedura: Esaminare lo stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

## <a name="examine-an-exception"></a><a name="exception"></a> Esaminare un'eccezione

Quando l'app genera un'eccezione, il debugger passa alla riga di codice che ha generato l'eccezione.

![Helper eccezioni](../debugger/media/dbg-tour-exception-helper.png "Helper eccezioni")

In questo esempio l'**Helper eccezioni** visualizza un'eccezione `System.Argument` e un messaggio di errore che indica che il formato del percorso non è valido. È chiaro quindi che l'errore si è verificato in un argomento di metodo o funzione.

In questo esempio l'errore è stato restituito dalla chiamata di `DirectoryInfo` a causa di una stringa vuota archiviata nella variabile `value`.

L'Helper eccezioni è un'ottima funzionalità che può facilitare il debug degli errori. La funzionalità consente di eseguire anche altre operazioni, ad esempio visualizzare i dettagli dell'errore e aggiungere un'espressione di controllo. Oppure, se necessario, è possibile modificare le condizioni che determinano la generazione di una particolare eccezione. Per altre informazioni su come gestire le eccezioni nel codice, vedere [Tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md).

> [!NOTE]
> L'Helper eccezioni ha sostituito Informazioni sulle eccezioni a partire da [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Espandere il nodo **Impostazioni eccezioni** per vedere altre opzioni relative alla gestione di questo tipo di eccezione, ma non apportare alcuna modifica per questa presentazione.

## <a name="configure-debugging"></a>Configurare il debug

È possibile configurare il progetto per la compilazione come [configurazione di debug o di rilascio](../debugger/how-to-set-debug-and-release-configurations.md), per configurare le proprietà del progetto per il debug o per configurare [le impostazioni generali](../debugger/how-to-specify-debugger-settings.md) per il debug. Inoltre, è possibile configurare il debugger in modo da visualizzare informazioni personalizzate utilizzando funzionalità come l'attributo [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) o, per C/C++, il [Framework NatVis](create-custom-views-of-native-objects.md).

Le proprietà di debug sono specifiche per ogni tipo di progetto. Ad esempio, è possibile specificare un argomento da passare all'applicazione all'avvio. È possibile accedere alle proprietà specifiche del progetto facendo clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e selezionando **Proprietà**. Le proprietà di debug vengono in genere visualizzate nella scheda **Compila** o **debug** , a seconda del tipo di progetto specifico.

![Proprietà progetto](../debugger/media/dbg-tour-project-properties.png "Proprietà progetto")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Debug di app ASP.NET attive nel servizio app di Azure

il **snapshot debugger** acquisisce uno snapshot delle app in produzione quando il codice a cui si è interessati viene eseguito. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

![Avviare Snapshot Debugger](../debugger/media/snapshot-launch.png "Avviare Snapshot Debugger")

La raccolta di snapshot è disponibile per le applicazioni ASP.NET in esecuzione nel servizio app di Azure. Per le applicazioni ASP.NET è necessario .NET Framework 4.6.1 o versione successiva, mentre per le applicazioni ASP.NET Core è necessario .NET Core 2.0 o versione successiva in Windows.

Per altre informazioni, vedere [Debug live ASP.NET apps using the Snapshot Debugger](../debugger/debug-live-azure-applications.md) (Eseguire il debug di app ASP.NET attive usando Snapshot Debugger).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Visualizzare snapshot con la funzionalità per tornare indietro di IntelliTrace (Visual Studio Enterprise)

La **funzionalità per tornare indietro di IntelliTrace** crea automaticamente uno snapshot dell'applicazione in corrispondenza di ogni evento di punto di interruzione ed esecuzione di passaggio del debugger. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

È possibile esplorare e visualizzare gli snapshot tramite i pulsanti **Vai indietro** e **Vai avanti** sulla barra degli strumenti di Debug. Questi pulsanti consentono di spostarsi tra gli eventi visualizzati nella scheda **Eventi** della finestra **Strumenti di diagnostica**.

![Pulsanti avanti e indietro passaggio](../debugger/media/intellitrace-step-back-icons-description.png  "Pulsanti avanti e indietro passaggio")

Per altre informazioni, vedere la pagina [Visualizzare lo stato precedente dell'applicazione con IntelliTrace](../debugger/view-historical-application-state.md).

## <a name="debug-performance-issues"></a>Problemi di prestazioni di debug

Se l'app viene eseguita troppo lentamente o usa una quantità eccessiva di memoria, potrebbe essere necessario testare l'app con gli strumenti di profilatura in anticipo. Per altre informazioni sugli strumenti di profilatura, ad esempio lo strumento utilizzo CPU e l'analizzatore memoria, vedere [prima di tutto gli strumenti di profilatura](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stata offerta una breve panoramica di molte funzionalità del debugger. È possibile esaminare in modo più approfondito una di queste funzionalità, i punti di interruzione.

> [!div class="nextstepaction"]
> [Informazioni sull'uso dei punti di interruzione](../debugger/using-breakpoints.md)
