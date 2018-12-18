---
title: "Utilizzo della finestra attività | Documenti Microsoft"
ms.custom: 
ms.date: 04/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c4ec0178a4767e7e0c5c726816dcd7088e14f17b
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="using-the-tasks-window"></a>Utilizzo della finestra Attività
Il **attività** finestra simile di **thread** finestra, ad eccezione del fatto che mostra informazioni sugli <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](/cpp/parallel/concrt/reference/task-group-class), o [winjs. Promise ](http://msdn.microsoft.com/library/windows/apps/br211867.aspx) oggetti anziché ogni thread. Analogamente ai thread, le attività rappresentano operazioni asincrone eseguibili simultaneamente; tuttavia, più attività possono essere eseguite nello stesso thread. 
  
 Nel codice gestito, è possibile utilizzare il **attività** finestra quando si lavora con <xref:System.Threading.Tasks.Task?displayProperty=fullName> oggetti o con il **await** e **async** parole chiave (**Await** e **Async** in Visual Basic). Per ulteriori informazioni sulle attività nel codice gestito, vedere [programmazione parallela](/dotnet/standard/parallel-programming/index).  
  
 Nel codice nativo, è possibile utilizzare il **attività** finestra quando si lavora con [gruppi di attività](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [gli algoritmi paralleli](/cpp/parallel/concrt/parallel-algorithms), [agenti asincroni](/cpp/parallel/concrt/asynchronous-agents), e [attività leggere](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Per ulteriori informazioni sulle attività nel codice nativo, vedere [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime).  
  
 In JavaScript, è possibile utilizzare la finestra attività quando si lavora con promessa `.then` codice. Vedere [programmazione asincrona in JavaScript (app UWP)](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx) per ulteriori informazioni.   
  
 È possibile utilizzare il **attività** finestra ogni volta che inserisce nel debugger. È possibile accedervi nel **Debug** menu facendo **Windows** e quindi fare clic su **attività**. La figura seguente mostra il **attività** finestra nella modalità predefinita.  
  
 ![Finestra attività](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
>  Nel codice gestito, un oggetto <xref:System.Threading.Tasks.Task> con lo stato <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus> o <xref:System.Threading.Tasks.TaskStatus> potrebbe non essere visualizzato nella finestra Attività quando i thread gestiti si trovano nello stato sospensione o join.  
  
## <a name="tasks-column-information"></a>Informazioni nelle colonne della finestra Attività  
 Le colonne di **attività** finestra Mostra le informazioni seguenti.  
  
|Nome colonna|Descrizione|  
|-----------------|-----------------|  
|**Flag**|Mostra quali attività sono contrassegnate e consente di impostare o rimuovere un flag per un'attività.|  
|**Icone**|Una freccia gialla indica l'attività corrente. L'attività corrente è l'attività in primo piano nel thread corrente.<br /><br /> Una freccia bianca indica l'attività di interruzione, vale a dire l'attività corrente al momento della chiamata del debugger.<br /><br /> L'icona di sospensione indica un'attività bloccata dall'utente. È possibile bloccare e sbloccare un'attività facendovi clic sopra con il pulsante destro del mouse nell'elenco.|  
|**ID**|Numero fornito dal sistema per l'attività. Nel codice nativo, è l'indirizzo dell'attività.|  
|**Status**|Stato corrente dell'attività (pianificata, attiva, in deadlock, in attesa o completata). Un'attività pianificata è un'attività che non è stata ancora eseguita, pertanto non dispone ancora di uno stack di chiamate, un thread assegnato o informazioni correlate.<br /><br /> Un'attività attiva è un'attività che stava eseguendo codice prima dell'accesso al debugger.<br /><br /> Un'attività in attesa è un'attività bloccata in quanto sta attendendo la segnalazione di un evento, il rilascio di un blocco o la conclusione di un'altra attività.<br /><br /> Un'attività in deadlock è un'attività in attesa il cui thread è in deadlock con un altro thread.<br /><br /> Passare il mouse su di **stato** cella di un'attività in deadlock o in attesa visualizzare ulteriori informazioni sul blocco. **Avviso:** il **attività** finestra segnala un deadlock solo per un'attività bloccata che utilizza una primitiva di sincronizzazione supportata da Wait Chain Traversal (WCT). Ad esempio, per un deadlock <xref:System.Threading.Tasks.Task> oggetto, che utilizza WCT, il debugger viene segnalato **bloccata in attesa**. Per un'attività in deadlock gestita dal Runtime di concorrenza, che non utilizza WCT, il debugger viene segnalato **in attesa**. Per ulteriori informazioni su WCT, vedere [Wait Chain Traversal](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Ora di inizio**|Ora in cui l'attività è diventata attiva.|  
|**Durata**|Numero di secondi durante i quali l'attività è rimasta attiva.|  
|**Tempo di completamento**|Ora in cui l'attività è stata completata.|  
|**Percorso**|Percorso corrente nello stack di chiamate dell'attività. Passare il mouse su questa cella per visualizzare l'intero stack di chiamate dell'attività. Le attività pianificate non presentano alcun valore in questa colonna.|  
|**Task**|Metodo iniziale ed eventuali argomenti passati all'attività quando è stata creata.|  
|**Elemento padre**|ID dell'attività che ha creato questa attività. Se la cella è vuota significa che l'attività non dispone di un'attività padre. Questo dato è applicabile ai soli programmi gestiti.|  
|**Assegnazione di thread**|ID e nome del thread nel quale viene eseguita l'attività.|  
|**Stato restituito**|Stato dell'attività quando è stata completata. I valori di stato restituito sono **successo**, **annullato**, e **errore**.|  
|**AppDomain**|Dominio applicazione nel quale viene eseguita l'attività, in caso di codice gestito.|  
|**task_group**|Per il codice nativo, l'indirizzo del [task_group](/cpp/parallel/concrt/reference/task-group-class.mdd) che ha pianificato l'attività. Per gli agenti asincroni e le attività leggere, questa colonna viene impostata su 0.|  
|Process|ID del processo in cui viene eseguita l'attività.|  
|Stato Async|Per il codice gestito, lo stato dell'attività. Per impostazione predefinita, questa colonna è nascosta. Per visualizzarla, aprire il menu di scelta rapida per una delle intestazioni di colonna. Scegliere **colonne**, **AsyncState**.|  
  
 Per aggiungere colonne alla visualizzazione, fare clic con il pulsante destro del mouse su un'intestazione di colonna e selezionare le colonne desiderate. Per rimuovere le colonne, annullare le selezioni. È possibile inoltre riordinare le colonne trascinandole a sinistra o a destra. Nell'illustrazione seguente viene mostrato il menu di scelta rapida delle colonne.  
  
 ![Menu visualizzazione collegamenti nella finestra attività in](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Ordinamento delle attività  
 Per ordinare le attività in base ai criteri delle colonne, fare clic sull'intestazione di colonna. Ad esempio, facendo clic di **ID** intestazione di colonna, è possibile ordinare le attività in base all'ID attività: 1,2,3,4,5 e così via. Per invertire l'ordine, fare nuovamente clic sull'intestazione. La colonna di ordinamento e l'ordinamento correnti sono indicati da una freccia nella colonna.  
  
## <a name="grouping-tasks"></a>Raggruppamento delle attività  
 È possibile raggruppare le attività in base a una qualsiasi colonna nella visualizzazione elenco. Ad esempio, facendo clic con il **stato** intestazione di colonna e quindi fare clic su **Raggruppa per stato**, è possibile raggruppare tutte le attività che hanno lo stesso stato. Tale operazione può risultare utile, ad esempio, per visualizzare rapidamente tutte le attività in attesa, così da concentrarsi sul motivo del blocco. È possibile inoltre comprimere un gruppo di poco interesse durante la sessione di debug. Allo stesso modo, è possibile raggruppare in base alle altre colonne. Per contrassegnare o rimuovere il contrassegno di un gruppo, è sufficiente fare clic sul pulsante accanto all'intestazione del gruppo. La figura seguente mostra il **attività** finestra nella modalità raggruppata.  
  
 ![Modalità raggruppata nella finestra attività in](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Visualizzazione padre/figlio  
 (Questa visualizzazione è disponibile solo per codice gestito). Facendo clic su un'intestazione di colonna e quindi facendo clic su **visualizzazione padre/figlio**, è possibile modificare l'elenco di attività per una visualizzazione gerarchica, in cui ogni elemento figlio è un nodo secondario che può essere visualizzato o nascosto nell'elemento padre. Nell'illustrazione seguente vengono mostrate le attività nella visualizzazione padre/figlio.  
  
 ![Padre &#45; visualizzare nella finestra delle attività figlio](../debugger/media/parallel_tasks_parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Contrassegno delle attività  
 È possibile contrassegnare il thread in cui un'attività è in esecuzione selezionando l'attività elemento dell'elenco e quindi scegliendo **Flag** dal menu di scelta rapida oppure facendo clic sull'icona del flag nella prima colonna. Se si contrassegnano diverse attività, sarà successivamente possibile ordinare in base alla colonna del contrassegno in modo da portare tutte le attività contrassegnate in cima e potersi concentrare su di esse. È inoltre possibile utilizzare il **stack in parallelo** consente di visualizzare solo le attività con contrassegno. In questo modo si possono filtrare le attività di poco interesse per il debug. I contrassegni non vengono salvati in modo permanente tra una sessione di debug e l'altra.  
  
## <a name="freezing-and-thawing-tasks"></a>Blocco e sblocco delle attività  
 È possibile bloccare il thread in cui viene eseguita un'attività facendo clic l'elemento dell'elenco attività e quindi fare clic su **Blocca Thread assegnato**. (Se un'attività è già bloccata, il comando è **Sblocca Thread assegnato**.) Quando si blocca un thread, questo non verrà eseguito nel momento in cui si proseguirà con l'esecuzione del codice dopo il punto di interruzione corrente. Il **bloccare tutti i thread, ma questo** comando Blocca tutti i thread eccetto quello che esegue l'elemento dell'elenco attività.  
  
 Nell'illustrazione seguente vengono mostrate le altre voci di menu per ogni attività.  
  
 ![Menu thread collegamenti nella finestra attività in](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Programmazione parallela](/dotnet/standard/parallel-programming/index)   
 [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime)   
 [Utilizzando la finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md)   
 [Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)