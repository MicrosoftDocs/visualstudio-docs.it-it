---
title: ParallelForEach&lt;T&gt; ActivityDesigner | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62d86499296c72f48d1ffcad932e9f1ff4d2fef1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach&lt;T&gt; ActivityDesigner
L'attività <xref:System.Activities.Statements.ParallelForEach%601> enumera gli elementi di una raccolta ed esegue in parallelo un'istruzione incorporata per ogni elemento della raccolta, ovvero in modo asincrono sullo stesso thread. Usare questa attività di controllo del flusso anziché l'attività <xref:System.Activities.Statements.Sequence> se si prevede che le relative attività figlio diventeranno inattive.

 L'attività <xref:System.Activities.Statements.ParallelForEach%601> include una proprietà <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> contenente un'espressione [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] specificata dall'utente. L'attività <xref:System.Activities.Statements.ParallelForEach%601> valuta tale proprietà in seguito al completamento di ogni ramo. Se restituisce **true**, quindi il <xref:System.Activities.Statements.ParallelForEach%601> attività viene completata senza eseguire gli altri rami. Se il <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> non restituisce **true**, quindi il <xref:System.Activities.Statements.ParallelForEach%601> attività viene completata quando tutte le relative attività figlio sono stati completati.

## <a name="the-parallelforeacht-activity"></a>L'attività ParallelForEach < T\> attività
 <xref:System.Activities.Statements.ParallelForEach%601> enumera i propri valori e pianifica l'elemento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> per ogni valore in cui viene enumerata. Esegue la pianificazione solo per l'elemento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. La modalità di esecuzione del corpo varia a seconda che <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> diventi o meno inattivo.

 Se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> non diventa inattivo, viene eseguito in ordine inverso in quanto le attività pianificate vengono gestite come uno stack, con l'ultima attività pianificata eseguita per prima. Ad esempio, se si dispone di una raccolta di {1,2,3,4} in <xref:System.Activities.Statements.ParallelForEach%601> e utilizzare un **WriteLine** come corpo in cui scrivere il valore. Nella console l'ordine di stampa sarà 4, 3, 2, 1 In questo modo **WriteLine** non diventa inattivo e pertanto, dopo 4 **WriteLine** pianificazione delle quattro attività, queste vengono eseguite utilizzando un comportamento dello stack (first in last-out).

 Il processo cambia se invece le attività incluse in <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> possono diventare inattive, come nel caso delle attività <xref:System.ServiceModel.Activities.Receive> o <xref:System.Activities.Statements.Delay>. Quindi non è necessario attenderne il completamento. <xref:System.Activities.Statements.ParallelForEach%601> passa all'attività corpo pianificata successiva e prova a eseguirla. Se anche questa attività diventa inattiva, <xref:System.Activities.Statements.ParallelForEach%601> passa ancora alla successiva attività Body.

### <a name="using-the-parallelforeacht-activity-designer"></a>Utilizzo di ParallelForEach\<T > ActivityDesigner
 Il **ParallelForEach\<T >** ActivityDesigner, vedere il **flusso di controllo** categoria del **della casella degli strumenti**, accessibile facendo clic di  **Casella degli strumenti** scheda sul lato sinistro del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **ParallelForEach\<T >** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie di attacco ogni volta che vengono in genere posizionate le attività, per esempio, all'interno di un **sequenza** ActivityDesigner. Dopo averlo rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], viene creato un <xref:System.Activities.Statements.ParallelForEach%601> attività, che per impostazione predefinita contiene un <xref:System.Activities.Activity.DisplayName%2A> di **ParallelForEach < Int32\>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T\> proprietà nella finestra di progettazione del flusso di lavoro
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.ParallelForEach%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è **ParallelForEach\<Int32 >**. Il valore può essere modificato facoltativamente nel **proprietà** griglia o direttamente nell'intestazione dell'ActivityDesigner.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Attività da eseguire per ogni elemento della raccolta. Per aggiungere il <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> attività, trascinare un'attività dalla casella degli strumenti nel **corpo** casella il **ParallelForEach\<T >** ActivityDesigner con testo di suggerimento "Rilasciare l'attività".|
|**TypeArgument**|True|Il tipo degli elementi di <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> raccolta specificata dal parametro generico *T*. Per impostazione predefinita, **TypeArgument** è impostato su **Int32**. Per modificare il tipo T nella **ParallelForEach < T\>**  ActivityDesigner, modificare il valore della **TypeArgument** casella combinata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Raccolta di elementi da scorrere. Per impostare il <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, digitare un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] espressione il **valori** casella il **ForEach < T\>**  ActivityDesigner nella casella con il testo di suggerimento "Immettere un'espressione VB" o in **Valori** casella il **proprietà** finestra.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Valutato al termine di ogni iterazione. Se restituisce true, le iterazioni in sospeso pianificate vengono annullate. Se questa proprietà non è impostata, tutte le istruzioni pianificate vengono eseguite fino al completamento.|

 Per impostazione predefinita, l'iteratore del ciclo è denominato item. È possibile modificare il nome della variabile di iteratore nel **ForEach** casella **ParallelForEach\<T >** ActivityDesigner. L'iteratore del ciclo può essere usato nelle espressioni contenute in elementi figlio dell'attività <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Vedere anche

- [sequenza](../workflow-designer/sequence-activity-designer.md)
- [Parallelo](../workflow-designer/parallel-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)