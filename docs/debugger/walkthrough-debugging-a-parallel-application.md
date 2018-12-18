---
title: 'Procedura dettagliata: Debug di un''applicazione parallela | Documenti Microsoft'
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b05192c2d57c280cef970d4b8887ff7eadbb27b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio"></a>Procedura dettagliata: Debug di un'applicazione parallela in Visual Studio
Questa procedura dettagliata viene illustrato come utilizzare il **attività in parallelo** e **stack in parallelo** windows per eseguire il debug di un'applicazione parallela. Queste finestre consentono di comprendere e verificare il comportamento di runtime del codice che usa il [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime). Nella procedura dettagliata viene fornito un esempio di codice con punti di interruzione incorporati. Dopo il codice si interrompe, la procedura dettagliata viene illustrato come utilizzare il **attività in parallelo** e **stack in parallelo** windows esaminarlo.  
  
 Nella procedura dettagliata vengono spiegate le seguenti attività:  
  
-   Come visualizzare gli stack di chiamate di tutti i thread in un'unica visualizzazione.  
  
-   Come visualizzare l'elenco delle istanze di `System.Threading.Tasks.Task` create nell'applicazione.  
  
-   Come visualizzare gli stack di chiamate reali delle attività anziché dei thread.  
  
-   Come passare al codice dal **attività in parallelo** e **stack in parallelo** windows.  
  
-   Come le finestre affrontano il ridimensionamento tramite il raggruppamento, lo zoom e altre funzionalità correlate.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Questa procedura dettagliata si presuppone che **Just My Code** è abilitata (è abilitata per impostazione predefinita nelle versioni più recenti di Visual Studio). Nel **strumenti** menu, fare clic su **opzioni**, espandere il **debug** nodo, seleziona **generale**e quindi selezionare **abilitare Just My Code (solo gestito)**. Se non si imposta questa funzionalità, si può comunque utilizzare la procedura dettagliata, ma è possibile che i risultati differiscano dalle illustrazioni.  
  
## <a name="c-sample"></a>Esempio in C#  
 Se si utilizza l'esempio in C#, la procedura dettagliata presuppone inoltre che il codice esterno sia nascosto. Per attivare o disattivare la visualizzazione del codice esterno, fare doppio clic su di **nome** intestazione della tabella di **Stack di chiamate** finestra e quindi selezionare o deselezionare **Mostra codice esterno**. Se non si imposta questa funzionalità, si può comunque utilizzare la procedura dettagliata, ma è possibile che i risultati differiscano dalle illustrazioni.  
  
## <a name="c-sample"></a>Esempio in C++  
 Se si utilizza l'esempio in C++, è possibile ignorare i riferimenti al codice esterno contenuti in questo argomento. Il codice esterno si applica solo all'esempio in C#.  
  
## <a name="illustrations"></a>Illustrazioni  
 Le illustrazioni contenute in questo argomento sono state registrate in un computer quad core che esegue l'esempio in C#. Benché sia possibile utilizzare altre configurazioni per completare questa procedura dettagliata, le illustrazioni potrebbero differire dalle schermate visualizzate sul computer in uso.  
  
## <a name="creating-the-sample-project"></a>Creazione del progetto di esempio  
 L'esempio di codice riportato in questa procedura dettagliata è relativo a un'applicazione che non esegue alcuna operazione. L'obiettivo è semplicemente comprendere come utilizzare le finestre degli strumenti per eseguire il debug di un'applicazione parallela.  
  
#### <a name="to-create-the-sample-project"></a>Per creare il progetto di esempio  
  
1.  In Visual Studio scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.  
  
2.  Nel **modelli installati** riquadro, selezionare Visual c#, Visual Basic o Visual C++. Per i linguaggi gestiti, assicurarsi che [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] sia visualizzato nella casella del framework.  
  
3.  Selezionare **applicazione Console** e quindi fare clic su **OK**. Restare nella configurazione per il debug, ovvero l'impostazione predefinita.  
  
4.  Aprire il file di codice con estensione CPP, CS o VB nel progetto. Eliminarne il contenuto per creare un file di codice vuoto.  
  
5.  Incollare il seguente codice per il linguaggio selezionato nel file di codice vuoto.  
  
 [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
 [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
 [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]  
  
1.  Nel **File** menu, fare clic su **Salva tutto**.  
  
2.  Nel **compilare** menu, fare clic su **Ricompila soluzione**.  
  
     Notare che vi sono quattro chiamate a `Debugger.Break` (`DebugBreak` nell'esempio C++). Pertanto, non è necessario inserire punti di interruzione; la semplice esecuzione dell'applicazione determinerà fino a quattro interruzioni nel debugger.  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>Utilizzo della finestra Stack in parallelo: visualizzazione Thread  
 Scegliere **Avvia debug** dal menu **Debug**. Attendere che venga raggiunto il primo punto di interruzione.  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Per visualizzare lo stack di chiamate di un singolo thread  
  
1.  Nel **Debug** dal menu **Windows** e quindi fare clic su **thread**. Ancorare il **thread** finestra nella parte inferiore di Visual Studio.  
  
2.  Nel **Debug** dal menu **Windows** e quindi fare clic su **Stack di chiamate**. Ancorare il **Stack di chiamate** finestra nella parte inferiore di Visual Studio.  
  
3.  Fare doppio clic su un thread di **thread** finestra per renderla corrente. I thread correnti presentano una freccia gialla. Quando si modifica il thread corrente, il relativo stack di chiamate viene visualizzato nel **Stack di chiamate** finestra.  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>Per esaminare la finestra Stack in parallelo  
  
1.  Nel **Debug** dal menu **Windows** e quindi fare clic su **stack in parallelo**. Assicurarsi che **thread** è selezionata nella casella nell'angolo superiore sinistro.  
  
     Tramite il **stack in parallelo** finestra, è possibile visualizzare gli stack di chiamate più contemporaneamente in una vista. La figura seguente mostra il **stack in parallelo** finestra precedente il **Stack di chiamate** finestra.  
  
     ![Visualizzazione nella finestra Stack in parallelo thread](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")  
  
     Lo stack di chiamate del thread principale viene visualizzato in una casella, mentre gli stack di chiamate degli altri quattro thread sono raggruppati in un'altra casella. I quattro thread vengono raggruppati insieme in quanto i rispettivi stack frame condividono gli stessi contesti del metodo, vale a dire si trovano negli stessi metodi: `A`, `B` e `C`. Per visualizzare gli ID di thread e i nomi dei thread che condividono la stessa casella, passare il mouse sull'intestazione (**4 thread**). Il thread corrente viene visualizzato in grassetto, come mostrato nell'illustrazione seguente.  
  
     ![Descrizione comandi che mostra i nomi e degli ID thread](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")  
  
     La freccia gialla indica lo stack frame attivo del thread corrente. Per ottenere ulteriori informazioni, passarvi sopra il mouse.  
  
     ![Descrizione comandi nello stack frame attivo](../debugger/media/pdb_walkthrough_1b.png "PDB_Walkthrough_1B")  
  
     È possibile impostare il livello di dettaglio da visualizzare per i frame dello stack (**i nomi dei moduli**, **tipi di parametro**, **i nomi dei parametri**, **i valori dei parametri**, **Numeri di riga** e **offset dei Byte**) facendo clic di **Stack di chiamate** finestra.  
  
     Un'evidenziazione blu attorno a una casella indica che il thread corrente è parte di quella casella. Il thread corrente è inoltre indicato dallo stack frame in grassetto nella descrizione comandi. Se si fa doppio clic sul thread principale nella finestra thread, è possibile osservare che l'evidenziazione blu nella **stack in parallelo** finestra si sposta di conseguenza.  
  
     ![Il thread principale nella finestra Stack in parallelo evidenziato](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Per riprendere l'esecuzione fino al secondo punto di interruzione  
  
1.  Per riprendere l'esecuzione fino a quando non viene raggiunto il secondo punto di interruzione, scegliere il **Debug** menu, fare clic su **continua**. L'illustrazione seguente mostra l'albero del thread in corrispondenza del secondo punto di interruzione.  
  
     ![Finestra Stack in parallelo molti rami](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")  
  
     In corrispondenza del primo punto di interruzione, i quattro thread erano passati tutti dal metodo S.A a S.B e a S.C. Che le informazioni sono ancora visibili nel **stack in parallelo** finestra, ma i quattro thread sono avanzati. Uno di essi ha proseguito fino a S.D, quindi a S.E. Un altro ha proseguito fino a S.F, S.G e S.H. Gli altri due hanno proseguito fino a S.I e S.J, dopo di che uno è passato a S.K mentre l'altro ha proseguito fino al codice esterno non utente.  
  
     È possibile passare il mouse sull'intestazione della casella, ad esempio, **1 Thread** o **2 thread**, per visualizzare gli ID dei thread. Passando invece il mouse sugli stack frame, verranno visualizzati gli ID dei thread e altri dettagli sui frame. L'evidenziazione blu indica il thread corrente, mentre la freccia gialla indica lo stack frame attivo del thread corrente.  
  
     L'icona con i fili (linee ondulate di colore blu e rosso sovrapposte) indica gli stack frame attivi dei thread non correnti. Nel **Stack di chiamate** fare doppio clic su s per passare i frame. Il **stack in parallelo** finestra indica lo stack frame corrente del thread corrente utilizzando un'icona di freccia circolare verde.  
  
     Nel **thread** finestra, passare tra i thread e osservare che la visualizzazione di **stack in parallelo** finestra viene aggiornata.  
  
     È possibile passare a un altro thread o a un altro frame di un altro thread, tramite il menu di scelta rapida nel **stack in parallelo** finestra. Ad esempio, fare doppio clic su s. j, scegliere **passa al Frame**, quindi fare clic su un comando.  
  
     ![Percorso di esecuzione degli stack in parallelo](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")  
  
     Fare doppio clic su s. c e scegliere **passa al Frame**. Uno dei comandi presenta un segno di spunta che indica lo stack frame del thread corrente. È possibile passare a quel frame dello stesso thread (si sposterà soltanto la freccia verde) oppure passare all'altro thread (si sposterà anche l'evidenziazione blu). Nell'illustrazione seguente viene mostrato il sottomenu.  
  
     ![Menu stack con 2 opzioni su C mentre J è corrente](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")  
  
     Quando un contesto del metodo è associato un unico stack frame, viene visualizzato nell'intestazione della casella **1 Thread** e passare a esso facendo doppio clic su. Facendo doppio clic su un contesto del metodo al quale sono associati più frame, verrà visualizzato automaticamente il menu. Passando il mouse sui contesti del metodo, notare il triangolo nero sulla destra. Il menu di scelta rapida verrà visualizzato anche facendo clic su quel triangolo.  
  
     Nel caso di applicazioni di grandi dimensioni con molti thread, è possibile concentrarsi su un unico sottoinsieme di thread. Il **stack in parallelo** finestra è possibile visualizzare gli stack di chiamate solo per i thread con flag. Sulla barra degli strumenti, fare clic su di **Mostra solo con contrassegno** pulsante accanto alla casella di elenco.  
  
     ![Finestra Stack in parallelo e della descrizione comando vuoti](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")  
  
     Successivamente, nel **thread** finestra, contrassegnare i thread uno a uno per vedere come i rispettivi stack di chiamate vengono visualizzati nel **stack in parallelo** finestra. Per contrassegnare i thread, utilizzare il menu di scelta rapida o la prima cella di un thread. Fare clic su di **Mostra solo con contrassegno** pulsante della barra degli strumenti per visualizzare tutti i thread.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Per riprendere l'esecuzione fino al terzo punto di interruzione  
  
1.  Per riprendere l'esecuzione fino a quando non viene raggiunto il terzo punto di interruzione, scegliere il **Debug** menu, fare clic su **continua**.  
  
     Se più thread si trovano nello stesso metodo ma questo, a sua volta, non si trovava all'inizio dello stack di chiamate, il metodo viene visualizzato in caselle diverse. Un esempio in corrispondenza del punto di interruzione corrente è S.L, il quale contiene tre thread e viene visualizzato in tre caselle. Fare doppio clic su S.L.  
  
     ![Percorso di esecuzione nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")  
  
     Si noti che S.L appare in grassetto nelle altre due caselle, così da poter vedere in quali altri punti viene visualizzato. Se si desidera visualizzare quali frame chiamano in s. l appare e quali sono le chiamate, fare clic su di **attiva/disattiva visualizzazione metodo** sulla barra degli strumenti. Nella figura seguente mostra la visualizzazione del metodo di **stack in parallelo** finestra.  
  
     ![Visualizzazione metodo nella finestra Stack in parallelo](../debugger/media/pdw_walkthrough_4.png "PDW_Walkthrough_4")  
  
     Si noti come il diagramma sia imperniato sul metodo selezionato e lo abbia posizionato nella propria casella al centro della visualizzazione. I chiamati e i chiamanti vengono visualizzati nella parte superiore e in quella inferiore. Fare clic su di **attiva/disattiva visualizzazione metodo** nuovo pulsante per uscire da questa modalità.  
  
     Menu di scelta rapida del **stack in parallelo** finestra seguente è disponibile anche altri elementi.  
  
    -   **Visualizzazione esadecimale** attiva o disattiva i numeri nelle descrizioni comandi tra decimale ed esadecimale.  
  
    -   **Informazioni sul caricamento dei simboli** e **impostazioni simboli** aprire le finestre di dialogo corrispondente.  
  
    -   **Vai a codice sorgente** e **Vai a Disassembly** spostarsi nell'editor per il metodo selezionato.  
  
    -   **Mostra codice esterno** Visualizza tutti i frame anche se non sono nel codice utente. Provare questa voce per vedere il diagramma espandersi per accogliere i frame aggiuntivi, i quali possono essere disattivati in quanto non si dispone di simboli per tali frame.  
  
     Quando si dispone di diagrammi di grandi dimensioni e si avanza al punto di interruzione successivo, è possibile far sì che la visualizzazione scorra automaticamente fino allo stack frame attivo del thread corrente, vale a dire il thread che per primo ha raggiunto il punto di interruzione. Nel **stack in parallelo** finestra, assicurarsi che il **scorrimento automatico a Stack Frame corrente** pulsante sulla barra degli strumenti.  
  
     ![Scorrimento automatico nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_4a.png "PDB_Walkthrough_4A")  
  
2.  Prima di continuare, nel **stack in parallelo** finestra, scorrere fino in fondo a sinistra e verso il basso.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Per riprendere l'esecuzione fino al quarto punto di interruzione  
  
1.  Per riprendere l'esecuzione fino al quarto punto di interruzione viene raggiunto, nel **Debug** menu, fare clic su **continua**.  
  
     Si noti come la visualizzazione sia scorsa automaticamente fino al punto in questione. Passare da un thread nel **thread** finestra o passare da uno stack frame nel **Stack di chiamate** finestra e notare come la visualizzazione scorra sempre automaticamente al frame corretto. Disattivare **scorrimento automatico a stack Frame corrente** opzione e osservare la differenza.  
  
     Il **vista aerea** risulta inoltre utile con diagrammi di grandi dimensioni nel **stack in parallelo** finestra. È possibile visualizzare il **vista aerea** fare clic sul pulsante tra le barre di scorrimento nell'angolo in basso a destra della finestra, come illustrato nella figura seguente.  
  
     ![Aerea &#45; occhio visualizzare nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")  
  
     È possibile spostare il rettangolo per avere una rapida panoramica del diagramma.  
  
     Un altro modo per spostare il diagramma in una direzione qualsiasi è fare clic su un'area vuota del diagramma e trascinarlo nel punto desiderato.  
  
     Per lo zoom avanti e indietro del diagramma, tenere premuto CTRL mentre si muove la rotella del mouse. In alternativa, fare clic sul pulsante Zoom nella barra degli strumenti, quindi utilizzare lo strumento Zoom.  
  
     ![Ingrandita stack nella finestra Stack in parallelo in](../debugger/media/pdb_walkthrough_5a.png "PDB_Walkthrough_5A")  
  
     È anche possibile visualizzare gli stack in una direzione dall'alto in basso, anziché dal basso in alto, facendo clic di **strumenti** , quindi scegliendo **opzioni**e quindi selezionare o deselezionare l'opzione nel **debug** nodo.  
  
2.  Prima di continuare, scegliere il **Debug** menu, fare clic su **Termina debug** per terminare l'esecuzione.  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Utilizzo della finestra Attività in parallelo e della visualizzazione Attività della finestra Stack in parallelo  
 Prima di proseguire, si consiglia di completare le procedure precedenti.  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Per riavviare l'applicazione fino al raggiungimento del primo punto di interruzione  
  
1.  Nel **Debug** menu, fare clic su **Avvia debug** e attendere che venga raggiunto il primo punto di interruzione.  
  
2.  Nel **Debug** dal menu **Windows** e quindi fare clic su **thread**. Ancorare il **thread** finestra nella parte inferiore di Visual Studio.  
  
3.  Nel **Debug** dal menu **Windows** e fare clic su **Stack di chiamate**. Ancorare il **Stack di chiamate** finestra nella parte inferiore di Visual Studio.  
  
4.  Fare doppio clic su un thread di **thread** rende corrente della finestra. I thread correnti presentano la freccia gialla. Quando si modifica il thread corrente, le altre finestre vengono aggiornate. Si esamineranno quindi le attività.  
  
5.  Nel **Debug** dal menu **Windows** e quindi fare clic su **attività in parallelo**. La figura seguente mostra il **attività** finestra.  
  
     ![Quattro esegue le attività nella finestra attività](../debugger/media/pdw_walkthrough_6.png "PDW_Walkthrough_6")  
  
     Per ogni attività in esecuzione è possibile visualizzare il relativo ID, restituito dalla proprietà omonima, l'ID e il nome del thread che la esegue e il relativo percorso (passando il mouse sul percorso viene visualizzata una descrizione comandi con l'intero stack di chiamate). Inoltre, sotto il **attività** colonna, è possibile visualizzare il metodo passato nell'attività, in altre parole, il punto iniziale.  
  
     Le colonne possono essere ordinate. Si noti il glifo di ordinamento che indica la colonna e la direzione di ordinamento. È anche possibile riordinare le colonne trascinandole a sinistra o a destra.  
  
     La freccia gialla indica l'attività corrente. Per passare da un'attività all'altra, fare doppio clic su un'attività o utilizzare il menu di scelta rapida. Quando si passa da un'attività all'altra, il thread sottostante diventa quello corrente e le altre finestre vengono aggiornate.  
  
     Quando si passa manualmente da un'attività a un'altra, la freccia gialla si sposta, ma una freccia bianca continua a mostrare l'attività che ha causato l'interruzione nel debugger.  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Per riprendere l'esecuzione fino al secondo punto di interruzione  
  
1.  Per riprendere l'esecuzione fino a quando non viene raggiunto il secondo punto di interruzione, scegliere il **Debug** menu, fare clic su **continua**.  
  
     In precedenza, il **stato** colonna tutte le attività venivano indicate come in esecuzione, ma ora due attività sono in attesa. Le attività possono essere bloccate per molte ragioni diverse. Nel **stato** colonna, passare il mouse su un'attività in attesa per conoscere il motivo per cui è bloccata. Ad esempio, nell'illustrazione seguente, l'attività 3 è in attesa dell'attività 4.  
  
     ![Due attività in attesa nella finestra attività in](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")  
  
     L'attività 4, a sua volta, è in attesa di un monitoraggio di proprietà del thread assegnato all'attività 2.  
  
     ![Attività in attesa e descrizione comando nella finestra attività in](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")  
  
     È possibile contrassegnare un'attività facendo clic sul contrassegno nella prima colonna del **attività** finestra.  
  
     È possibile utilizzare i contrassegni per tenere traccia delle attività tra diversi punti di interruzione nella stessa sessione di debug o per filtrare le attività il cui stack di chiamate vengono visualizzati di **stack in parallelo** finestra.  
  
     Quando si utilizza il **stack in parallelo** finestra precedente, è possibile visualizzarne i thread dell'applicazione. Visualizzazione di **stack in parallelo** nuovamente finestra, ma questa volta Visualizza le attività dell'applicazione. Eseguire questa operazione selezionando **attività** nella casella in alto a sinistra. Nell'illustrazione che segue viene mostrata la visualizzazione Attività.  
  
     ![Visualizzazione nella finestra Stack in parallelo thread](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")  
  
     I thread che attualmente non eseguono attività non vengono mostrati nella visualizzazione dell'attività di **stack in parallelo** finestra. Inoltre, per i thread che eseguono attività, alcuni stack frame che non sono importanti per le attività vengono filtrati dalla parte superiore e dalla parte inferiore dello stack.  
  
     Visualizzazione di **attività** nuovamente finestra. Fare clic con il pulsante destro del mouse su un'intestazione di colonna qualsiasi per visualizzare un menu di scelta rapida per la colonna.  
  
     ![Menu visualizzazione collegamenti nella finestra attività in](../debugger/media/pdb_walkthrough_8a.png "PDB_Walkthrough_8A")  
  
     Il menu di scelta rapida può essere utilizzato per aggiungere o rimuovere colonne. Ad esempio, la colonna AppDomain non è selezionata, pertanto non viene visualizzata nell'elenco. Fare clic su **padre**. Il **padre** colonna viene visualizzata senza valori per le quattro attività.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Per riprendere l'esecuzione fino al terzo punto di interruzione  
  
1.  Per riprendere l'esecuzione fino a quando non viene raggiunto il terzo punto di interruzione, scegliere il **Debug** menu, fare clic su **continua**.  
  
     Una nuova attività, l'attività 5, è ora in esecuzione mentre l'attività 4 è in attesa. È possibile visualizzare il motivo, passare il mouse sull'attività in attesa nella **stato** finestra. Nel **padre** colonna, si noti che l'attività 4 è il padre dell'attività 5.  
  
     Per visualizzare meglio la relazione padre-figlio, fare doppio clic su di **padre** intestazione di colonna e quindi fare clic su **visualizzazione padre/figlio**. Si dovrebbe vedere l'illustrazione seguente.  
  
     ![Padre &#45; visualizzare nella finestra delle attività figlio](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")  
  
     Si noti che l'attività 4 e l'attività 5 sono in esecuzione nello stesso thread. Queste informazioni non vengono visualizzate nel **thread** finestra; fatto che appaia qui è un altro vantaggio del **attività** finestra. A tale scopo, è possibile visualizzare il **stack in parallelo** finestra. Assicurarsi che si sta visualizzando **attività**. Individuare le attività 4 e 5 facendo doppio clic su essi nel **attività** finestra. In questo caso, l'evidenziazione blu **stack in parallelo** finestra viene aggiornata. È inoltre possibile individuare le attività 4 e 5 analizzando le descrizioni comandi nel **stack in parallelo** finestra.  
  
     ![Attività di visualizzazione nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")  
  
     Nel **stack in parallelo** , fare doppio clic su s. p e quindi fare clic su **passa a Thread**. La finestra passerà alla visualizzazione Thread e verrà visualizzato il thread corrispondente. È possibile vedere entrambe le attività nello stesso thread.  
  
     ![Thread nella visualizzazione thread evidenziato](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")  
  
     Si tratta di un altro vantaggio della visualizzazione attività nella **stack in parallelo** rispetto alla finestra di **thread** finestra.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Per riprendere l'esecuzione fino al quarto punto di interruzione  
  
1.  Per riprendere l'esecuzione fino a quando non viene raggiunto il terzo punto di interruzione, scegliere il **Debug** menu, fare clic su **continua**. Fare clic su di **ID** intestazione di colonna per ordinare in base a ID. Si dovrebbe vedere l'illustrazione seguente.  
  
     ![Quattro stati nella finestra Stack in parallelo di attività](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")  
  
     Essendo stata completata, l'attività 5 non viene più visualizzata. Se ciò non avviene nel computer in uso e il deadlock non viene visualizzato, avanzare di un passaggio premendo F11.  
  
     Le attività 3 e 4 sono ora in attesa una dell'altra e sono in deadlock. Vi sono inoltre 5 nuove attività che sono attività figlio dell'attività 2 e vengono ora pianificate. Le attività pianificate sono attività avviate nel codice ma non ancora eseguite. Di conseguenza, i relativi **percorso** e **assegnazione Thread** colonne sono vuote.  
  
     Visualizzazione di **stack in parallelo** nuovamente finestra. L'intestazione di ogni casella presenta una descrizione comandi nella quale sono visualizzati gli ID e i nomi dei thread. Passare alla visualizzazione attività nella **stack in parallelo** finestra. Passare il mouse su un'intestazione per visualizzare l'ID, il nome e lo stato dell'attività come mostrato nell'illustrazione seguente.  
  
     ![Descrizione comando dell'intestazione nella finestra Stack in parallelo](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")  
  
     È possibile raggruppare le attività in base alle colonne. Nel **attività** finestra, fare doppio clic su di **stato** intestazione di colonna e quindi fare clic su **Raggruppa per stato**. La figura seguente mostra il **attività** finestra raggruppati per stato.  
  
     ![Nella finestra attività in attività raggruppate](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")  
  
     È anche possibile raggruppare in base alle altre colonne. Raggruppando le attività, è possibile concentrarsi su un subset di attività. Ogni gruppo comprimibile presenta un conteggio degli elementi raggruppati insieme. È anche possibile contrassegnare rapidamente tutti gli elementi nel gruppo facendo clic di **Flag** pulsante a destra del **Comprimi** pulsante.  
  
     ![Raggruppati stack nella finestra Stack in parallelo in](../debugger/media/pdb_walkthrough_12a.png "PDB_Walkthrough_12A")  
  
     L'ultima funzionalità del **attività** finestra da esaminare è il menu di scelta rapida che viene visualizzato quando si fa clic su un'attività.  
  
     ![Menu di scelta rapida nella finestra attività in](../debugger/media/pdb_walkthrough_12b.png "PDB_Walkthrough_12B")  
  
     Il menu di scelta rapida visualizza comandi diversi a seconda dello stato dell'attività. I comandi possono includere **copia**, **Seleziona tutto**, **visualizzazione esadecimale**, **passare all'attività**, **bloccare assegnato Thread**, **bloccare tutti i thread, ma il**, e **Sblocca Thread assegnato**, e **Flag**.  
  
     È possibile bloccare il thread sottostante di un'attività o di più attività oppure bloccare tutti i thread a eccezione di quello assegnato. Un thread bloccati vengono rappresentati nel **attività** finestra perché è nel **thread** finestra, da un oggetto blu *sospendere* icona.  
  
## <a name="summary"></a>Riepilogo  
 Questa procedura dettagliata è illustrato il **attività in parallelo** e **stack in parallelo** finestre del debugger. Utilizzare queste finestre con progetti reali che a loro volta utilizzano codice multithreading. È possibile esaminare codice parallelo scritto in C++, C# o Visual Basic.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug delle applicazioni multithreading](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Programmazione parallela](/dotnet/standard/parallel-programming/index)   
 [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime)   
 [Utilizzando la finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md)   
 [Uso della finestra Attività](../debugger/using-the-tasks-window.md)