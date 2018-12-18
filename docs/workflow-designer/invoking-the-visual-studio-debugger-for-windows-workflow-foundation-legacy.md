---
title: Richiamare il Debugger di Visual Studio per Windows Workflow Foundation (Legacy) | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e3563b175359e00a051138451292eb015958480
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)
Questo argomento viene descritto come utilizzare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugger per eseguire il debug [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] applicazioni in Progettazione flussi di lavoro Windows legacy. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Il debug dei flussi di lavoro legacy viene in genere eseguito nello stesso modo in cui si esegue il debug di programmi scritti negli altri linguaggi di programmazione di Visual Studio. È possibile avviare il debugger di [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] per Windows Workflow Foundation nei modi seguenti:

-   Selezionare **Connetti a processo** sul **Debug** menu per selezionare un'istanza del flusso di lavoro in esecuzione dai processi disponibili.

-   Premere **F5** per avviare un'istanza del flusso di lavoro o di continuare l'esecuzione dopo aver raggiunto un punto di interruzione.

## <a name="stepping-through-code"></a>Avanzamento tramite codice
 Il debugger supporta una delle procedure di debug più comuni, l’avanzamento, che consiste nell'esecuzione di una riga di codice alla volta. Esistono tre comandi di avanzamento tramite codice:

-   **Passaggio In**: È possibile avanzare in un'altra attività usando **F11**. Il debugger avanza in qualsiasi gestore definito. Se nessun gestore è definito, viene eseguita l'istruzione/routine dell'attività oppure, con CompositeActivity contenenti altre attività, viene eseguita l'istruzione della prima attività in stato di esecuzione. L'esecuzione di istruzioni in gestori del codice dalla finestra di progettazione non è supportata per le attività seguenti: **IfElseActivity**, **l'attività WhileActivity**, **ConditionedActivityGroup**, o **ReplicatorActivity**. Per eseguire il debug dei gestori associati a queste attività è necessario inserire punti di interruzione espliciti nel codice.

-   **Esci da istruzione /**: È possibile uscire da un'altra attività usando **MAIUSC + F11**. Uscendo da un'istruzione/routine di un'attività, l'attività corrente e tutte le relative attività di pari livello vengono eseguite fino al completamento. Il debugger reimposta quindi il padre dell'attività corrente. Uscendo da un gestore del codice, il debugger reimposta l'attività alla quale è associato il gestore.

-   **Esegui istruzione/routine**: È possibile passare a un'altra attività usando **F10**. Quando si passa a un'altra attività composta. Il debugger reimposta il primo figlio eseguibile dell'attività composta. Quando si passa a una diversa da CompositeActivity, ad esempio un **CodeActivity** attività, il debugger esegue l'attività e relativi gestori ad essa associati e le interruzioni di attività successiva. Se l'attività eseguita è l'ultima attività figlio di un'attività composta, dopo l'esecuzione il debugger reimposterà l'attività padre.

## <a name="attaching-to-a-process"></a>Connessione a un processo
 Per eseguire il debug di un flusso di lavoro tramite il collegamento a un processo, selezionare il processo disponibile dal **processi disponibili** casella di riepilogo di **Connetti a processo** la finestra di dialogo. Se **automatico: codice del flusso di lavoro** non viene visualizzata nella **allegarvi** testo casella, quindi fare clic su **selezionare**. Nel **Seleziona tipo di codice** la finestra di dialogo, fare clic su **eseguire il Debug di questi tipi di codice** e selezionare **flusso di lavoro**. Quindi fare clic su **OK** e fare clic su **collegamento**.

## <a name="debugging-with-f5"></a>Debug con F5
 Se un'applicazione host del flusso di lavoro e flusso di lavoro DLL si trovano in diversi progetti di Visual Studio, ad esempio, quando si utilizza una libreria di attività del flusso di lavoro, è necessario impostare il progetto DLL del flusso di lavoro come progetto di avvio delle soluzioni Visual Studio per eseguire il debug del flusso di lavoro utilizzando **F5**. È inoltre necessario impostare il percorso all'applicazione host del progetto di DLL del flusso di lavoro **Avvia programma esterno** proprietà.

 Per impostare un progetto di avvio in Esplora soluzioni, il nome del progetto e scegliere **imposta come progetto di avvio**. Per impostare il percorso all'host di **Avvia programma esterno** proprietà, fare doppio clic del flusso di lavoro **proprietà** nodo in Esplora soluzioni e selezionare il **Debug** scheda. In **azione di avvio**selezionare **Avvia programma esterno** e immettere il percorso del file .exe che ospita il flusso di lavoro che si desidera eseguire il debug.

 Se l'applicazione host è impostata come progetto di avvio, solo il debugger di Visual Studio viene richiamato per l'esecuzione del debug. Il debugger di [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] per Windows Workflow Foundation non viene richiamato. Se viene usato il debugger di Visual Studio, vengono eseguiti solo i punti di interruzione del codice C# o di Visual Basic, mentre i punti di interruzione impostati nella finestra di progettazione del flusso di lavoro non vengono eseguiti. Ad esempio, un punto di interruzione impostato su un'attività <xref:System.Workflow.Activities.ParallelActivity> nella finestra di progettazione verrà eseguito se viene usato il debugger di [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] per Windows Workflow Foundation, ma non quando si usa il debugger di Visual Studio.

## <a name="see-also"></a>Vedere anche

- [Procedura: Impostare punti di interruzione nei flussi di lavoro (legacy)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)