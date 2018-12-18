---
title: Introduzione al debug di applicazioni multithreading con | Documenti Microsoft
ms.custom: H1HackMay2017
ms.date: 06/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 067f28cfbc90d26088b37eb40b730edca37533d2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="get-started-debugging-a-multithreaded-application-in-visual-studio"></a>Introduzione al debug di un'applicazione multithreading in Visual Studio
Visual Studio fornisce numerosi strumenti e gli elementi dell'interfaccia utente per eseguire il debug di applicazioni multithreading. In questa esercitazione viene illustrato come utilizzare gli indicatori dei thread, il **stack in parallelo** finestra il **espressioni di controllo parallelo** finestra punti di interruzione condizionali e i punti di interruzione di filtro. In questa esercitazione richiede solo pochi minuti, ma il suo completamento consentirà di acquisire familiarità con le funzionalità per il debug di applicazioni multithreading.

|         |         |
|---------|---------|
|  ![icona della telecamera](../install/media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) sul debug con multithreading che illustra una procedura simile. |

Altri argomenti forniscono informazioni aggiuntive sull'utilizzo di altri strumenti di debug con multithreading:

- Per un argomento simile in cui viene illustrato come utilizzare il **posizione di Debug** barra degli strumenti e **thread** finestra, vedere [procedura dettagliata: Debug di un'applicazione multithreading](../debugger/how-to-use-the-threads-window.md).

- Per un argomento simile con un esempio che usa <xref:System.Threading.Tasks.Task> (codice gestito) e il runtime di concorrenza (C++), vedere [procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md). Per suggerimenti di debug generali che si applicano ai tipi di applicazione più multithreading, leggere questo argomento sia l'argomento collegato.
  
Per iniziare questa esercitazione, è necessario un progetto di applicazione multithreading. Per creare tale progetto, attenersi alla procedura qui indicata.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Per creare il progetto di applicazione multithreading  
  
1.  Nel **File** menu, scegliere **New** e quindi fare clic su **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Nel **tipo di progetto**s, fare clic sulla lingua di preferenza: **Visual c#**, **Visual C++**, o **Visual Basic**.  
  
3.  Nel **modelli** scegliere **App Console**.  
  
4.  Nel **nome** casella, digitare il nome MyThreadWalkthroughApp.  
  
5.  Fare clic su **OK**.  
  
     Verrà visualizzato un nuovo progetto console. Dopo aver creato il progetto, viene visualizzato un file di origine. A seconda del linguaggio scelto, il file di origine potrebbe essere chiamato Module1. vb, Program.cs o MyThreadWalkthroughApp.cpp.  
  
6.  Eliminare il codice che viene visualizzato nel file di origine e sostituirlo con il codice di esempio illustrato di seguito.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  Nel **File** menu, fare clic su **Salva tutto**.  
  
#### <a name="to-begin-the-tutorial"></a>Per iniziare l'esercitazione  
  
-   Nell'editor del codice sorgente, cercare il codice seguente: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>Per avviare il debug  
  
1.  Fare clic nella barra di navigazione a sinistra del `Thread.Sleep` o `Thread::Sleep` istruzione per inserire un nuovo punto di interruzione.  
  
     Nella barra di navigazione sul lato sinistro dell'editor del codice sorgente, verrà visualizzato un cerchio rosso. che indica l'impostazione di un punto di interruzione in tale posizione. 
  
2.  Nel **Debug** menu, fare clic su **Avvia debug** (**F5**).  
  
     Visual Studio compila la soluzione, l'app viene avviata l'esecuzione con il debugger collegato e quindi l'applicazione si arresta nel punto di interruzione.  
  
    > [!NOTE]
    > Se si passa lo stato attivo alla finestra della console, fare clic su di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] finestra per ripristinare lo stato attivo per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Nell'editor del codice sorgente, individuare la riga che contiene il punto di interruzione:  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Per individuare il marcatore del thread  

1.  Nella barra degli strumenti di Debug, fare clic su di **Mostra thread nell'origine** pulsante ![Mostra thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Premere **F11** una volta per spostare la riga di un debugger del codice.
  
3.  All'estrema sinistra della finestra, In questa riga, verrà visualizzato un *marcatore del thread* icona ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") che due fili. Il marcatore del thread indica l'interruzione di un thread in questa posizione.

    Si noti che un marcatore del thread potrebbe essere parzialmente nascosta da un punto di interruzione. 
  
4.  Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati. in cui è indicato il nome e il numero ID di ciascun thread interrotto. In questo caso, il nome è probabilmente `<noname>`. 
  
5.  Fare clic sul marcatore del thread per visualizzare le opzioni disponibili nel menu di scelta rapida.
    
## <a name="ParallelStacks"></a>Consente di visualizzare il percorso di thread

Nel **stack in parallelo** finestra, è possibile passare tra una visualizzazione thread e (per la programmazione basata su attività), visualizzazione attività ed è possibile visualizzare informazioni sullo stack di chiamate per ogni thread. In questa app, è possibile usare la visualizzazione dei thread.

1. Aprire il **stack in parallelo** finestra scegliendo **Debug > Windows > stack in parallelo**. Dovrebbe essere simile al seguente (le informazioni esatte sarà diverse a seconda della posizione corrente di ogni thread, l'hardware e il linguaggio di programmazione).

    ![Finestra Stack in parallelo](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    In questo esempio, da sinistra a destra è ottenere queste informazioni:
    
    - Il thread principale (lato sinistro) è stato arrestato sul `Thread.Start` (il punto di interruzione è indicato dall'icona marcatore thread ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Due thread di avere immesso il `ServerClass.InstanceMethod`, uno dei quali è il thread corrente (freccia gialla), mentre l'altro thread è stato arrestato `Thread.Sleep`.
    - Avvio di un nuovo thread (sulla destra) anche (è stato arrestato sul `ThreadHelper.ThreadStart`).

2.  Fare doppio clic su voci di **stack in parallelo** finestra per visualizzare le opzioni disponibili nel menu di scelta rapida.

    È possibile eseguire azioni diverse da questi menu di scelta rapida, ma per questa esercitazione verranno illustrati più di questi dettagli di **espressioni di controllo parallelo** finestra (sezioni successive).

    > [!NOTE]
    > Se si è più interessati a visualizzare un elenco di visualizzazione con informazioni su ogni thread, utilizzare il **thread** finestra invece. Vedere [procedura dettagliata: Debug di un'applicazione multithreading](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Impostare un'espressione di controllo in una variabile

1. Aprire il **espressioni di controllo parallelo** finestra scegliendo **Debug > Windows > espressioni di controllo parallelo > controllo1 parallelo**.

2. Fare clic sulla cella in cui viene visualizzato il `<Add Watch>` testo (o la cella di intestazione vuota nella colonna 4), tipo `data`, e premere INVIO.

    I valori per la variabile di dati per ogni thread vengono visualizzati nella finestra.

3. Fare di nuovo clic nella cella in cui viene visualizzato il `<Add Watch>` testo (o la cella di intestazione vuota nella colonna 5), tipo `count`, e premere INVIO.

    I valori per la variabile di conteggio per ogni thread vengono visualizzati nella finestra. (Se non viene visualizzato questo quantità di informazioni ancora, provare a premere F11 alcune altre volte per spostare l'esecuzione dei thread nel debugger.)

    ![Finestra Espressioni di controllo in parallelo](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Fare doppio clic su una delle righe nella finestra per visualizzare le opzioni disponibili.

## <a name="flagging-and-unflagging-threads"></a>Impostazione e rimozione dei flag dei thread  
È possibile contrassegnare i thread che si desidera prestare particolare attenzione. Contrassegno di thread è un buon metodo per tenere traccia dei thread importanti e per ignorare i thread che non si desidera eseguire.  
  
#### <a name="to-flag-threads"></a>Per impostare i flag dei thread  

1. Nel **espressioni di controllo parallelo** finestra, tenere premuto il tasto MAIUSC e selezionare più righe.

2. Mouse e scegliere **Flag**.

    A questo punto, tutti i thread selezionati vengono contrassegnati. A questo punto, è possibile filtrare per mostrare solo thread con flag.
  
3.  Nel **espressioni di controllo parallelo** finestra, trovare il **Mostra solo thread con flag** pulsante ![Mostra thread con flag](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Fare clic su di **Mostra solo thread con flag** pulsante.  
  
    Nell'elenco viene visualizzato ora solo il thread con flag.

    > [!TIP]
    > Quando si hanno alcuni thread con flag, è possibile fare doppio clic su una riga di codice nell'editor di codice e scegliere **eseguire i thread con flag fino al cursore** (assicurarsi di scegliere codice che tutti i thread con flag raggiungerà). Questo verrà sospendere i thread nella riga selezionata di codice, rendendo più semplice controllare l'ordine di esecuzione da [blocco e sblocco dei thread](#bkmk_freeze).

5.  Fare clic su di **Mostra solo thread con flag** pulsante per tornare alla **Mostra tutti i thread** modalità.
    
#### <a name="to-unflag-threads"></a>Per rimuovere i flag dei thread

Per rimuovere i flag dei thread, è possibile fare doppio clic su uno o più thread con flag nel **espressioni di controllo parallelo** finestra e scegliere **Rimuovi flag**.

## <a name="bkmk_freeze"></a> Blocco e sblocco dei esecuzione dei thread 

> [!TIP]
> È possibile bloccare e sbloccare (sospendere e riprendere) i thread per controllare l'ordine in cui i thread di eseguono operazioni. Ciò consente di risolvere i problemi di concorrenza, ad esempio i deadlock e race condition.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Per bloccare e sbloccare i thread  
  
1.  Nel **espressioni di controllo parallelo** finestra, con tutte le righe selezionate, fare clic e scegliere **bloccare**.

    Nella seconda colonna, pausa ora viene visualizzata un'icona per ogni riga. L'icona di sospensione indica che il thread è bloccato.

2.  Deselezionare le righe, fare clic su una sola riga.

3.  Fare doppio clic su una riga e selezionare **Sblocca**.

    L'icona di sospensione è stata risolta in questa riga, che indica che il thread non è bloccato.

4.  Passare all'editor di codice e fare clic su **F11**. Viene eseguito solo il thread non bloccato.

    L'app può anche creare un'istanza di alcuni nuovi thread. Si noti che tutti i nuovi thread senza flag e non sono bloccati.

## <a name="bkmk_follow_a_thread"></a> Seguire un Thread singolo con punti di interruzione condizionali

In alcuni casi, può essere utile seguire l'esecuzione di un singolo thread nel debugger. A tale scopo, è possibile bloccare i thread che non si è interessati in, ma in alcuni scenari è consigliabile seguire un singolo thread senza bloccare altri thread (per riprodurre un particolare, ad esempio bug). Per eseguire un thread senza bloccare altri thread, è necessario evitare l'interruzione del codice, ad eccezione nel thread in cui si è interessati. È possibile farlo impostando un [punto di interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

È possibile impostare i punti di interruzione in condizioni diverse, ad esempio il nome del thread o l'ID del thread. Un altro metodo che può risultare utile consiste nell'impostare la condizione sui dati che si conoscono univoci per ogni thread. Si tratta di uno scenario di debug comune, in cui si è più interessati in alcuni valori di dati specifico di in un particolare thread.

#### <a name="to-follow-a-single-thread"></a>Per eseguire un thread singolo

1. Il punto di interruzione creato in precedenza di mouse e scegliere **condizioni**.

2. Nel **impostazioni punto di interruzione** finestra `data == 5` per l'espressione condizionale.

    ![Punto di interruzione condizionale](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Se è più interessati a un thread specifico, utilizzare un nome o ID del thread per la condizione. Per eseguire questa operazione nel **impostazioni punto di interruzione** selezionare **filtro** anziché **espressione condizionale**e seguire i suggerimenti di filtro. Si consiglia di denominare i thread nel codice dell'app (dal momento che gli ID di thread modifichino quando si riavvia il debugger).

3. Chiudi il **impostazioni punto di interruzione** finestra.

4. Fare clic sul riavvio ![riavviare App](../debugger/media/dbg-tour-restart.png "RestartApp") per riavviare la sessione di debug.

    Verrà interrotta nel codice sul thread per il quale la variabile di dati è 5. Cercare la freccia gialla (contesto corrente del debugger) **espressioni di controllo parallelo** finestra per verificare che.

5. A questo punto, è possibile saltare il codice (F10) e passaggio al codice (F11) e seguire l'esecuzione del thread singolo.

    Fino a quando la condizione del punto di interruzione è univoca per il thread e il debugger non raggiunge qualsiasi altro punto di interruzione in altri thread (potrebbe essere necessario disabilitare le), è possibile saltare il codice e passaggio al codice senza dover passare agli altri thread.

    > [!NOTE]
    > Quando si arriva il debugger, vengono eseguiti tutti i thread. Tuttavia, il debugger non generi un'interruzione nel codice in altri thread, a meno che uno degli altri thread raggiunge un punto di interruzione. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Informazioni sulle finestre di debug con multithreading 

#### <a name="to-switch-to-another-thread"></a>Per passare a un altro thread 

- Per passare a un altro thread, vedere [procedura: passare a un altro Thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Per ulteriori informazioni sulle finestre Stack paralleli ed espressioni di controllo parallelo  
  
- Vedere [procedura: utilizzare la finestra Stack paralleli](../debugger/using-the-parallel-stacks-window.md) 

- Vedere [procedura: utilizzare la finestra Espressioni di controllo parallelo](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>Vedere anche  
 [Il debug di applicazioni a thread multipli](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
