---
title: 'Esercitazione: Eseguire il debug del codice C'
description: Informazioni su come avviare il debugger di Visual Studio, eseguire il codice un'istruzione alla volta ed esaminare i dati.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 01/31/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ede47c9daf37011195d66c746498cdfc809d24b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77027249"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Esercitazione: Informazioni sul debug del codice C# tramite Visual Studio

Questo articolo descrive le funzionalità del debugger di Visual Studio con una procedura dettagliata. Per una panoramica di alto livello delle funzionalità del debugger, vedere [Presentazione del debugger](../../debugger/debugger-feature-tour.md). Quando si esegue il *debug dell'app* in genere si esegue l'applicazione con il debugger collegato. Durante il debug, il debugger offre diversi modi per vedere le operazioni eseguite dal codice durante l'esecuzione. È possibile rivedere il codice ed esaminare i valori archiviati nelle variabili, impostare espressioni di controllo nelle variabili per rilevare le modifiche dei valori, esaminare il percorso di esecuzione del codice, verificare l'esecuzione di un ramo del codice e così via. Se è la prima volta che si esegue il debug del codice, può essere utile leggere [Debug per principianti](../../debugger/debugging-absolute-beginners.md) prima di procedere con questo articolo.

Sebbene l'app demo sia un'app C#, la maggior parte delle funzionalità è applicabile a C++, Visual Basic, F#, Python, JavaScript e altri linguaggi supportati da Visual Studio (F# non supporta la funzionalità Modifica e continuazione. F# e JavaScript non supportano la finestra **Auto**). Gli screenshot sono in linguaggio C#.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Avvio del debugger e raggiungimento dei punti di interruzione
> * Uso dei comandi per esaminare il codice nel debugger
> * Ispezione delle variabili nelle finestre dei suggerimenti dati e del debugger
> * Esaminare lo stack di chiamate

## <a name="prerequisites"></a>Prerequisites

::: moniker range=">=vs-2019"

È necessario disporre di Visual Studio 2019 installato e del carico di lavoro di sviluppo multipiattaforma .NET Core.You must have Visual Studio 2019 installed and the **.NET Core cross-platform development** workload.

::: moniker-end
::: moniker range="vs-2017"

È necessario disporre di Visual Studio 2017 installato e del carico di lavoro di sviluppo multipiattaforma .NET Core.You must have Visual Studio 2017 installed and the **.NET Core cross-platform development** workload.

::: moniker-end

::: moniker range="vs-2017"

Se Visual Studio non è già stato installato, passare alla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è già stato installato, passare alla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

Se è necessario installare il carico di lavoro ma si dispone già di Visual Studio, passare a **Strumenti** > **Get Tools and Features...**, che apre il programma di installazione di Visual Studio. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro di **sviluppo multipiattaforma .NET Core,** quindi scegliere **Modifica**.

## <a name="create-a-project"></a>Creare un progetto

In primo luogo, si creerà un progetto di applicazione console .NET Core.First, you'll create a .NET Core console application project. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Dalla barra dei menu superiore, scegliere **File** > **Nuovo** > **progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **C#** e quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Assegnare quindi al progetto il nome *get-started-debugging*.

     Se non viene visualizzato il modello di progetto **Applicazione console (.NET Core)**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

     Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio 2019.

   Se la finestra di avvio non è aperta, scegliere **Finestra di avvio** **file** > .

1. Nella finestra di avvio scegliere **Crea un nuovo progetto.**

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C# ** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato i filtri di linguaggio e piattaforma, scegliere il modello **App console (.NET Core)** e **Avanti**.

   ![Scegliere il modello di C ' per l'applicazione console (.NET Core)Choose the C' template for the Console App (.NET Core)](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Se il modello **App console (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**. Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.

1. Nella finestra **Configura il nuovo progetto digitare** o immettere *GetStartedDebugging* nella casella **Nome progetto.** Scegliere quindi **Crea,** quindi Crea .

   Visual Studio aprirà il nuovo progetto.
   
::: moniker-end

## <a name="create-the-application"></a>Creazione dell'applicazione

1. In *Program.cs*, sostituire tutto il codice predefinito con il codice seguente:

    ```csharp
    using System;
    class ArrayExample
    {
        static void Main()
        {
            char[] letters = { 'f', 'r', 'e', 'd', ' ', 's', 'm', 'i', 't', 'h'};
            string name = "";
            int[] a = new int[10];
            for (int i = 0; i < letters.Length; i++)
            {
                name += letters[i];
                a[i] = i + 1;
                SendMessage(name, a[i]);
            }
            Console.ReadKey();
        }
        static void SendMessage(string name, int msg)
        {
            Console.WriteLine("Hello, " + name + "! Count to " + msg);
        }
    }
    ```

## <a name="start-the-debugger"></a>Avviare il debugger.

1. Premere **F5** (**Debug > Avvia debug**) o il pulsante Avvia **debug** nella barra degli strumenti Debug. ![Start Debugging](../../debugger/media/dbg-tour-start-debugging.png "Avvia debug")

     **F5** avvia l'app con il debugger collegato al processo dell'app. Fino ad ora, tuttavia, non è stata eseguita alcuna operazione per esaminare il codice. Di conseguenza, viene semplicemente avviata l'app e viene visualizzato l'output della console.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     In questa esercitazione viene esaminata l'app usando il debugger e vengono descritte le funzionalità del debugger.

2. Arrestare il debugger premendo il pulsante rosso ![Stop Debugging](../../debugger/media/dbg-tour-stop-debugging.png "Debug") (**Shift** + **F5**).

3. Nella finestra della console, premere un tasto per chiudere la finestra della console.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

1. Nel ciclo `for` della funzione `Main` impostare un punto di interruzione facendo clic sul margine sinistro della riga di codice seguente:

    `name += letters[i];`

    Nel punto di interruzione del cerchio rosso viene visualizzato un punto di ![interruzione](../../debugger/media/dbg-breakpoint.png "Punto di interruzione") del cerchio rosso.

    I punti di interruzione sono una delle funzionalità più basilari ed essenziali del debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

2. Premere **F5** o il ![pulsante](../../debugger/media/dbg-tour-start-debugging.png "Avvia debug") **Avvia debug** , l'app viene avviata e il debugger viene eseguito sulla riga di codice in cui si imposta il punto di interruzione.

    ![Impostare e raggiungere un punto di interruzione](../csharp/media/get-started-set-breakpoint.png)

    La freccia gialla rappresenta l'istruzione in corrispondenza della quale il debugger si è interrotto e il punto in cui anche l'esecuzione dell'app viene sospesa (l'istruzione non è ancora stata eseguita).

     Se l'app non è ancora in esecuzione, **F5** avvia il debugger e lo arresta in corrispondenza del primo punto di interruzione. In caso contrario, **F5** continua l'esecuzione dell'app fino al punto di interruzione successivo.

    I punti di interruzione sono una funzionalità utile quando si conosce la riga di codice o la sezione di codice che si vuole esaminare nel dettaglio. Per informazioni sui diversi tipi di punti di interruzione che è possibile impostare, ad esempio i punti di interruzione condizionali, vedere [Utilizzo dei punti di interruzione](../../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Esplorare il codice nel debugger tramite i comandi di esecuzione

In questa esercitazione nella maggior parte dei casi vengono usati tasti di scelta rapida che rappresentano un modo rapido per eseguire l'app nel debugger (i comandi equivalenti, ad esempio i comandi di menu, sono indicati tra parentesi).

1. Durante `for` la pausa nel `Main` ciclo nel metodo, premere **F11** (o scegliere Esegui `SendMessage` debug > **Esegui**) due volte per passare alla chiamata al metodo.

     Dopo aver premuto **F11** due volte, si dovrebbe essere a questa riga di codice:

     `SendMessage(name, a[i]);`

1. Premere **F11** ancora una volta `SendMessage` per accedere al metodo.

     Il puntatore giallo `SendMessage` avanza nel metodo.

     ![Usare F11 per eseguire il codice da un'istruzione all'altroUse F11 to Step Into code](../csharp/media/get-started-f11.png "F10 Passo in")

     F11 corrisponde al comando **Esegui istruzione** e consente di eseguire l'app un'istruzione alla volta. F11 è un buon metodo per esaminare il flusso di esecuzione nel dettaglio. (Per spostarsi più velocemente nel codice, ti mostriamo anche altre opzioni.) Per impostazione predefinita, il debugger ignora il codice non utente (se si desiderano ulteriori dettagli, vedere [Just My Code](../../debugger/just-my-code.md)).

     Si supponga di aver eseguito `SendMessage` l'esame del metodo e di voler uscire dal metodo ma rimanere nel debugger. Questa operazione può essere eseguita usando il comando **Esci da istruzione/routine**.

1. Premere **MAIUSC** + **F11** (o **Eseguire il debug > esci da un controllo di sorpasso**).

     Questo comando riprende l'esecuzione dell'app (e fa avanzare il debugger) fino alla restituzione del metodo o della funzione corrente.

     È necessario tornare `for` nel ciclo `Main` nel metodo, `SendMessage` in pausa in corrispondenza della chiamata al metodo.

1. Premere **F11** più volte fino `SendMessage` a tornare alla chiamata al metodo.

1. Durante la pausa durante la chiamata al metodo, premere **F10** (o scegliere **Debug > eseguire l'istruzione/)** una volta.

     ![Usare F10 per eseguire il codice di istruzione/istruzione](../csharp/media/get-started-step-over.png "F10 Passo sopra")

     Si noti questa volta che `SendMessage` il debugger non esegue l'istruzione nel metodo. **F10** fa avanzare il debugger senza eseguire le istruzioni nelle funzioni o nei metodi del codice dell'app (il codice rimane in esecuzione). Premendo **F10** nella chiamata al metodo `SendMessage` anziché **F11**, è stato ignorato il codice di implementazione per `SendMessage` (non d'interesse ai fini dell'esercitazione). Per ulteriori informazioni sui diversi modi per spostarsi all'interno del codice, vedere [Esplorare il codice nel debugger](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Esplorare il codice con il pulsante per l'esecuzione fino alla riga selezionata dall'utente

1. Premere **F5** per passare nuovamente al punto di interruzione.

1. Nell'editor di codice scorrere verso `Console.WriteLine` il `SendMessage` basso e passare il puntatore del mouse sul metodo nel metodo fino a quando non viene visualizzato a sinistra il pulsante verde ![Esegui per](../../debugger/media/dbg-tour-run-to-click.png "Eseguire EseguiClic") **fare clic.** La descrizione comando per il pulsante è "Continua l'esecuzione fino a qui".

     ![Utilizzare la funzione Esegui con un clic](../csharp/media/get-started-run-to-click.png "Esegui fino alla riga selezionata")

   > [!NOTE]
   > Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è una nuova funzionalità di [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Se il pulsante freccia verde non viene visualizzato, usare **F11** in questo esempio per spostare il debugger nella posizione corretta.

2. Fare clic sul pulsante **Esegui per fare clic** su Esegui per fare clic su ![.](../../debugger/media/dbg-tour-run-to-click.png "Eseguire EseguiClic")

    Il debugger passa `Console.WriteLine` al metodo.

    L'uso di questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è uno strumento pratico per l'esplorazione rapida all'interno di un'area visibile del codice dell'app (è possibile fare clic in qualsiasi file aperto).

## <a name="restart-your-app-quickly"></a>Riavviare rapidamente l'app

Fare clic sul pulsante **Riavvia** ![app di riavvio](../../debugger/media/dbg-tour-restart.png "App di riavvio") nella barra degli strumenti Debug **(CTRL** + **Maiusc** + **F5**).

Il pulsante **Riavvia** consente di risparmiare tempo rispetto all'arresto dell'app e al riavvio del debugger. Il debugger viene messo in pausa in corrispondenza del primo punto di interruzione raggiunto eseguendo il codice.

Il debugger si arresta nuovamente in `for` corrispondenza del punto di interruzione impostato in precedenza all'interno del ciclo.

## <a name="inspect-variables-with-data-tips"></a>Esaminare le variabili con i suggerimenti dati

Le funzionalità che consentono di esaminare le variabili sono tra le funzionalità più utili del debugger e sono disponibili diversi modi per eseguire questa operazione. Spesso quando si tenta di eseguire il debug di un problema, si tenta di determinare se le variabili includono i valori previsti in un determinato momento.

1. Durante la pausa `name += letters[i]` sull'istruzione, `letters` passare il mouse sulla variabile e vedere il suo valore `char[10]`predefinito, il valore del primo elemento nella matrice, .

1. Espandere `letters` la variabile per visualizzarne le proprietà, che includono tutti gli elementi contenuti nella variabile.

1. Successivamente, passare `name` il mouse sulla variabile e viene visualizzato il relativo valore corrente, una stringa vuota.

1. Premere **F5** (o **Debug** > **Continue**) alcune volte `for` per scorrere più volte il ciclo, `name` mettendo nuovamente in pausa il punto di interruzione e passando il mouse sulla variabile ogni volta per controllarne il valore.

     ![Visualizzare un suggerimento dati](../csharp/media/get-started-data-tip.gif "Visualizzare un suggerimento dati")

     Il valore della variabile cambia a `for` seconda dell'iterazione `fr`del `fre`ciclo, visualizzando i valori di `f`, quindi , quindi , e così via.

     Spesso, durante il debug, è necessario controllare rapidamente i valori delle proprietà sulle variabili, per vedere se si stanno archiviando i valori previsti, e i suggerimenti dati costituiscono un valido strumento per questa operazione.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Esaminare le variabili con le finestre Auto e Variabili locali

1. Osservare la finestra **Auto** nella parte inferiore dell'editor di codice.

    Se è chiuso, aprirlo mentre è in pausa nel debugger scegliendo **Esegui debug** > **delle impostazioni automatiche**di**Windows** > .

    Nella finestra **Auto** vengono visualizzate le variabili e i relativi valori correnti. La finestra **Auto** mostra tutte le variabili usate nella riga corrente o nella riga precedente (vedere la documentazione per il comportamento specifico del linguaggio).

1. Osservare quindi la finestra **Variabili locali** in una scheda accanto alla finestra **Auto**.

1. Espandere `letters` la variabile per visualizzare gli elementi in essa contenuti.

     ![Esaminare le variabili nella finestra Variabili locali](../csharp/media/get-started-locals-window.png "finestra Variabili locali")

    La finestra **Variabili locali** mostra le variabili presenti nell'[ambito](https://www.wikipedia.org/wiki/Scope_(computer_science)) corrente, ovvero il contesto di esecuzione corrente.

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

1. Nella finestra principale dell'editor di `name` codice fare clic con il pulsante destro del mouse sulla variabile e scegliere **Aggiungi controllo .**

    Viene visualizzata la finestra **Espressione di controllo** nella parte inferiore dell'editor di codice. È possibile usare una finestra **Espressione di controllo** per specificare una variabile (o un'espressione) che si vuole controllare.

    A questo punto, si `name` dispone di un orologio impostato sulla variabile e si può vedere la sua modifica del valore come ci si sposta attraverso il debugger. A differenza di altre finestre delle variabili, la finestra **Espressione di controllo** mostra sempre le variabili controllate (che appaiono disattivate quando sono fuori ambito).

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

1. Mentre l'esecuzione è in pausa nel ciclo `for`, fare clic sulla finestra **Stack di chiamate**, visualizzata per impostazione predefinita nel riquadro inferiore destro.

    Se è chiuso, aprirlo mentre è in pausa nel debugger scegliendo **Esegui debug** > **stack di chiamate**di**Windows** > .

2. Fare clic su **F11** alcune volte fino `SendMessage` a quando il debugger viene sospeso nel metodo. Osservare la finestra **Stack di chiamate**.

    ![Esaminare lo stack di chiamate](../csharp/media/get-started-call-stack.png "EsaminareCallStackExamineCallStack")

    La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. La prima riga visualizza la funzione corrente (il metodo `SendMessage` in questa app). La seconda riga indica che `SendMessage` è stato chiamato dal metodo `Main` e così via.

   > [!NOTE]
   > La finestra **Stack di chiamate** è simile alla prospettiva di debug di alcuni IDE come Eclipse.

    Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

    È possibile fare doppio clic su una riga di codice per visualizzare il codice sorgente e modificare anche l'ambito corrente controllato dal debugger. Questa azione non fa avanzare il debugger.

    È anche possibile usare i menu di scelta rapida nella finestra **Stack di chiamate** per eseguire altre operazioni. Ad esempio, è possibile inserire i punti di interruzione nelle funzioni specificate, far avanzare il debugger usando **Esegui fino al cursore** e passare a esaminare il codice sorgente. Per altre informazioni, vedere [Procedura: Esaminare lo stack di chiamate](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

1. Premere **F11** due `Console.WriteLine` volte per eseguire il metodo.

1. Con il debugger sospeso `SendMessage` nella chiamata al metodo, utilizzare il mouse per afferrare la freccia gialla (il `Console.WriteLine`puntatore di esecuzione) a sinistra e spostare la freccia gialla in alto di una riga, tornando a .

1. Premere **F11**.

    Il debugger esegue nuovamente il metodo `Console.WriteLine` (visualizzato nell'output della finestra della console).

    Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

    > [!WARNING]
    > Spesso questa funzionalità deve essere usata con attenzione. Nella descrizione comando viene visualizzato un avviso. È anche possibile che vengano visualizzati altri avvisi. Non è possibile ripristinare uno stato precedente dell'applicazione spostando il cursore.

1. Premere **F5** per continuare a eseguire l'app.

    L'esercitazione è stata completata.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice ed esaminare le variabili. Sono disponibili una panoramica delle funzionalità del debugger e collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Primo sguardo al debugger](../../debugger/debugger-feature-tour.md)
