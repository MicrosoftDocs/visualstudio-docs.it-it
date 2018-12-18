---
title: Visualizzare la finestra Stack in parallelo tramite thread | Documenti Microsoft
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72c7c38dece8924f48298c0b7b661f564f9b1afc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="view-threads-and-tasks-using-the-parallel-stacks-window"></a>Visualizzazione thread e le attività tramite la finestra Stack in parallelo
Il **stack in parallelo** finestra è utile quando si esegue il debug di applicazioni multithreading. Il relativo **visualizzazione thread** Mostra informazioni sullo stack di chiamate per tutti i thread nell'applicazione. Consente di navigare tra i thread e gli stack frame nei thread. Nel codice gestito, il **visualizzazione attività** Mostra stack di chiamate di <xref:System.Threading.Tasks.Task?displayProperty=fullName> oggetti. Nel codice nativo, il **visualizzazione attività** Mostra stack di chiamate di [gruppi di attività](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [gli algoritmi paralleli](/cpp/parallel/concrt/parallel-algorithms), [agenti asincroni](/cpp/parallel/concrt/asynchronous-agents)e [attività leggere](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).  
  
## <a name="threads-view"></a>Visualizzazione Thread  
 Nell'illustrazione seguente viene mostrato un thread passato da principale ad A, quindi a B, infine a codice esterno. Altri due thread sono partiti da codice esterno per poi passare ad A, ma uno dei thread ha proseguito fino a B, quindi a codice esterno, mentre l'altro thread ha proseguito fino a C, quindi ad AnonymousMethod.  
  
 ![Visualizzazione nella finestra Stack in parallelo thread](../debugger/media/parallel_stacksthread.png "Parallel_StacksThread")  
  
 Nella figura, il percorso di chiamate del thread corrente è evidenziato in blu, e il percorso corrente (stack frame attivo) del thread viene indicato dalla freccia gialla. È possibile modificare lo stack frame corrente selezionando un metodo diverso nella **stack in parallelo** finestra. Ciò potrebbe comportare anche la modifica del thread corrente, a seconda che il metodo selezionato sia già parte del thread corrente o di un altro thread. Nella tabella seguente vengono descritte le principali funzionalità del **stack in parallelo** finestra come mostrato nell'illustrazione.  
  
|Lettera di riferimento|Nome elemento|Descrizione|  
|--------------------|------------------|-----------------|  
|A|Segmento o nodo dello stack di chiamate|Contiene una serie di metodi per uno o più thread. Se non vi sono righe della freccia connesse al nodo, questo rappresenta l'intero percorso di chiamate per i thread.|  
|B|Evidenziazione blu|Indica il percorso di chiamate del thread corrente.|  
|C|Righe della freccia|Connettono i nodi per costituire l'intero percorso di chiamate per i thread.|  
|D|Descrizione comandi nell'intestazione del nodo|Mostra l'ID e il nome definito dall'utente di ogni thread il cui percorso di chiamate condivide questo nodo.|  
|E|Metodo|Rappresenta uno o più stack frame nello stesso metodo.|  
|F|Descrizione comando (metodo)|Nella visualizzazione thread, Mostra tutti i thread in una tabella simile per la **thread** finestra. Nella visualizzazione attività sono visualizzate tutte le attività in una tabella simile per la **attività** finestra.|  
  
 Nella finestra Stack in parallelo viene inoltre un **vista aerea** icona nel riquadro principale quando il grafico è troppo grande per la finestra. È possibile fare clic sull'icona per visualizzare l'intero grafico nella finestra.  
  
## <a name="stack-frame-icons"></a>Icone di stack Frame  
 Nella tabella seguente vengono descritte le icone che forniscono informazioni sugli stack frame attivi e correnti:  
  
|||  
|-|-|  
|Icona|Descrizione|  
|![Freccia gialla in stack in parallelo](../debugger/media/icon_parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Indica che il metodo contiene il percorso corrente (stack frame attivo) del thread corrente.|  
|![Icona thread in stack in parallelo](../debugger/media/icon_parallelthreads.gif "Icon_ParallelThreads")|Indica che il metodo contiene il percorso corrente (stack frame attivo) di un thread non corrente.|  
|![Freccia verde in stack in parallelo](../debugger/media/icon_parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Indica che il metodo contiene lo stack frame corrente (il contesto di debug corrente). Il nome del metodo appare in grassetto in tutti i nodi nei quali viene visualizzato.|  
  
## <a name="toolbar-controls"></a>Controlli della barra degli strumenti  
 Nell'illustrazione e nella tabella che seguono sono descritti i controlli disponibili nella barra degli strumenti della finestra Stack in parallelo.  
  
 ![Barra degli strumenti nella finestra Stack in parallelo](../debugger/media/parallel_stackstoolbar.png "Parallel_StacksToolbar")  
  
|Lettera di riferimento|Control|Descrizione|  
|--------------------|-------------|-----------------|  
|A|Casella combinata Thread/Attività|Consente di passare dalla visualizzazione degli stack di chiamate dei thread alla visualizzazione degli stack di chiamate delle attività e viceversa. Per altre informazioni, vedere Visualizzazione Attività e Visualizzazione Thread.|  
|B|Mostra solo con contrassegno|Mostra gli stack di chiamate per i thread contrassegnati in altre finestre di debug, ad esempio il **thread GPU** finestra e **espressioni di controllo parallelo** finestra.|  
|C|Attiva/Disattiva visualizzazione metodo|Consente di passare dalla Visualizzazione stack alla Visualizzazione metodo e viceversa. Per ulteriori informazioni, vedere Visualizzazione metodo.|  
|D|Scorrimento automatico a stack frame corrente|Scorre automaticamente il diagramma in modo da visualizzare lo stack frame corrente. Questa funzionalità è utile quando si modifica lo stack frame corrente da altre finestre o quando si raggiunge un nuovo punto di interruzione nei diagrammi di grandi dimensioni.|  
|E|Attiva/Disattiva controllo zoom|Mostra o nasconde il controllo zoom. È inoltre possibile ingrandire premendo CTRL e ruotando la rotellina del mouse, indipendentemente dalla visibilità del controllo zoom, oppure utilizzando CTRL + MAIUSC + '+' per eseguire lo zoom avanti e CTRL + MAIUSC +'-' per eseguire lo zoom indietro. Premere CTRL + F8 comporterà l'ingrandimento per adattarlo alla schermata.|  
  
### <a name="context-menu-items"></a>Voci del menu di scelta rapida  
 Nell'illustrazione e nella tabella seguente vengono descritte le voci di menu di scelta rapida disponibili quando si fa clic su un metodo in visualizzazione thread o visualizzazione attività. Le ultime sei voci derivano direttamente dalla finestra Stack di chiamate e non introducono nuovi comportamenti.  
  
 ![Menu di scelta rapida nella finestra Stack in parallelo](../debugger/media/parallel_contmenu.png "Parallel_ContMenu")  
  
|MenuItem|Descrizione|  
|---------------|-----------------|  
|Flag|Contrassegna l'elemento selezionato.|  
|Rimuovi flag|Rimuove il flag dall'elemento selezionato.|  
|Blocca|Blocca l'elemento selezionato.|  
|Sblocca|Sblocca l'elemento selezionato.|  
|Passa ad attività (thread)|Esegue la stessa funzione della casella combinata nella barra degli strumenti, ma conserva lo stesso stack frame evidenziato.|  
|Vai a codice sorgente|Consente di passare al percorso nel codice sorgente che corrisponde allo stack frame sul quale l'utente ha fatto clic con il pulsante destro del mouse.|  
|Passa a frame|Uguale al comando di menu corrispondente nella finestra Stack di chiamate. Tuttavia, con stack in parallelo, più frame corrispondano a un metodo. La voce di menu dispone pertanto di sottomenu, ognuno dei quali rappresenta uno stack frame specifico. Se uno degli stack frame si trova nel thread corrente, verrà selezionato il menu che corrisponde a quello stack frame.|  
|Vai a disassembly|Consente di passare al percorso nella finestra Disassembly che corrisponde allo stack frame sul quale l'utente ha fatto clic con il pulsante destro del mouse.|  
|Mostra codice esterno|Mostra o nasconde il codice esterno.|  
|Visualizzazione esadecimale|Consente di passare dalla visualizzazione decimale a quella esadecimale e viceversa.|  
|Informazioni sul caricamento simboli|Consente di visualizzare la finestra di dialogo corrispondente.|  
|Impostazioni simboli|Consente di visualizzare la finestra di dialogo corrispondente.|  
  
## <a name="tasks-view"></a>Visualizzazione attività  
 Se l'applicazione utilizza <xref:System.Threading.Tasks.Task?displayProperty=fullName> oggetti (codice gestito) o `task_handle` oggetti (codice nativo) per esprimere il parallelismo, è possibile utilizzare la casella combinata nella barra degli strumenti finestra Stack in parallelo per passare alla *visualizzazione attività*. La visualizzazione Attività mostra gli stack di chiamate delle attività anziché dei thread. La visualizzazione Attività presenta le seguenti differenze rispetto alla visualizzazione Thread:  
  
-   Gli stack di chiamate dei thread che non eseguono attività non vengono visualizzati.  
  
-   Gli stack di chiamate dei thread che eseguono attività sono visivamente tagliati nella parte superiore e nella parte inferiore per visualizzare i frame più rilevanti che riguardano le attività.  
  
-   Quando più attività si trovano in un unico thread, gli stack di chiamate di tali attività vengono suddivisi in nodi separati.  
  
 Nell'illustrazione seguente vengono mostrate la visualizzazione Attività della finestra Stack in parallelo sulla destra e la corrispondente visualizzazione Thread sulla sinistra.  
  
 ![Attività di visualizzazione nella finestra Stack in parallelo](../debugger/media/parallel_tasksview.png "Parallel_TasksView")  
  
 Per visualizzare l'intero stack di chiamate, tornare semplicemente alla visualizzazione thread facendo clic su uno stack frame e scegliendo **passa a Thread**.  
  
 Come descritto nella tabella precedente, al passaggio del mouse su un metodo, è possibile visualizzare informazioni aggiuntive. Nell'immagine seguente sono mostrate le informazioni nella descrizione comandi per la visualizzazione Thread e la visualizzazione Attività.  
  
 ![Le descrizioni comandi nella finestra Stack in parallelo](../debugger/media/parallel_stack_tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Visualizzazione metodo  
 Dalla visualizzazione Thread o Attività è possibile ruotare il grafico sul metodo corrente facendo clic sull'icona Visualizzazione metodo nella barra degli strumenti. La visualizzazione metodo mostra immediatamente tutti i metodi in tutti i thread che chiamano o sono chiamati dal metodo corrente. Nell'illustrazione seguente viene mostrata una visualizzazione Thread e viene illustrato come le stesse informazioni appaiono nella visualizzazione metodo.  
  
 ![Visualizzazione metodo nella finestra Stack in parallelo](../debugger/media/parallel_methodview.png "Parallel_MethodView")  
  
 Passando a un nuovo stack frame, quel metodo diventa il metodo corrente e nella finestra vengono visualizzati tutti i chiamanti e i chiamati per il nuovo metodo. È possibile che, in conseguenza a ciò, alcuni thread compaiano o scompaiano dalla visualizzazione, a seconda che il metodo sia visualizzato nei relativi stack di chiamate. Per tornare alla visualizzazione Stack, fare nuovamente clic sul pulsante della barra degli strumenti Visualizzazione metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione al debug di un'applicazione multithreading](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Programmazione parallela](/dotnet/standard/parallel-programming/index)   
 [Utilizzo della finestra attività](../debugger/using-the-tasks-window.md)   
 [Classe di attività](../extensibility/debugger/task-class-internal-members.md)
