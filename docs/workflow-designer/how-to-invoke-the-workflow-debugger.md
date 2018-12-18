---
title: 'Procedura: richiamare il Debugger del flusso di lavoro | Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4865956c0c5929c817f55bf2bfa5aea76f4ef6f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Procedura: richiamare il debugger del flusso di lavoro.
Generalmente si esegue il debug dei flussi di lavoro nello stesso modo in cui si esegue il debug di programmi scritti negli altri linguaggi di programmazione di Visual Studio. È possibile avviare il debugger del flusso di lavoro nei modi seguenti:

-   Selezionare **Connetti a processo** sul **Debug** menu per selezionare il processo host in esecuzione per l'istanza del flusso di lavoro. La procedura è identica a quella di collegamento a un processo host nel codice gestito.

-   Premere **F5** per avviare un'istanza del flusso di lavoro o di continuare l'esecuzione dopo aver raggiunto un punto di interruzione.

-   Usare debug remoto. Per informazioni sul debug remoto, vedere [procedura: attivare il debug remoto](http://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > Se l'applicazione del flusso di lavoro destinata x86 architettura ed è ospitato in un computer che esegue un sistema operativo a 64 bit, il debug remoto non funzionerà a meno che non [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] è installato nel computer remoto o la destinazione per l'applicazione del flusso di lavoro viene modificato in **Qualsiasi CPU**.

### <a name="stepping-through-code"></a>Esecuzione di codice istruzione per istruzione

-   **Passaggio In**: È possibile avanzare in un'altra attività usando **F11**. Il debugger avanza in qualsiasi gestore definito. Se nessun gestore è definito, viene eseguita l'istruzione/routine dell'attività oppure, con CompositeActivity contenenti altre attività, viene eseguita l'istruzione della prima attività in stato di esecuzione.

-   **Esci:** è possibile uscire da un'altra attività usando **MAIUSC + F11**. Uscendo da un'istruzione/routine di un'attività, l'attività corrente e tutte le relative attività di pari livello vengono eseguite fino al completamento. Il debugger reimposta quindi il padre dell'attività corrente. Uscendo da un gestore del codice, il debugger reimposta l'attività alla quale è associato il gestore.

-   **Esegui istruzione/routine**: È possibile passare a un'altra attività usando **F10**. Quando viene eseguita l'istruzione/routine di un oggetto CompositeActivity, il debugger reimposta il primo figlio eseguibile del CompositeActivity. Quando viene eseguita l'istruzione/routine di un attività diversa da CompositeActivity, ad esempio <xref:System.Activities.Statements.Assign>, il debugger esegue l'attività e i gestori ad essa associati e reimposta l’attività successiva. Se l'attività eseguita è l'ultima attività figlio di un oggetto CompositeActivity, dopo l'esecuzione il debugger reimposterà l'attività padre.

### <a name="debugging-with-f5"></a>Debug con F5

-   Se si compila un progetto applicazione Console flusso di lavoro, è sufficiente premere **F5** per avviare il debug nell'applicazione e del flusso di lavoro. Se si compila una libreria attività autonomamente, è necessario usare come progetto di avvio un'applicazione host eseguibile. Per impostare un progetto di avvio in **Esplora**, il nome dell'host del progetto e scegliere **imposta come progetto di avvio**.

## <a name="see-also"></a>Vedere anche

- [Procedura: Impostazione di punti di interruzione nei Flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Debug dei flussi di lavoro mediante Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)