---
title: ActivityDesigner Parallel | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1c3f24af736dfd3762de7942ba1f52442dfd20c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="parallel-activity-designer"></a>ActivityDesigner Parallel
L'attività <xref:System.Activities.Statements.Parallel> esegue contemporaneamente una raccolta delle attività figlio.

## <a name="the-parallel-activity"></a>Attività Parallel
 L'attività <xref:System.Activities.Statements.Parallel> archivia le relative attività figlio in una raccolta <xref:System.Activities.Statements.Parallel.Branches%2A>. Usare l'attività <xref:System.Activities.Statements.Parallel> anziché l'attività <xref:System.Activities.Statements.Sequence> se alcune delle attività figlio possono diventare inattive.

 L'attività <xref:System.Activities.Statements.Parallel> include una proprietà <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> contenente un'espressione [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] specificata dall'utente. L'attività <xref:System.Activities.Statements.Parallel> valuta tale proprietà in seguito al completamento di ogni ramo. Se restituisce **True**, quindi il <xref:System.Activities.Statements.Parallel> attività viene completata senza eseguire gli altri rami. Se il <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> non restituisce **True**, quindi il <xref:System.Activities.Statements.Parallel> attività viene completata quando tutte le relative attività figlio sono stati completati.

### <a name="using-the-parallel-activity-designer"></a>Utilizzo dell'ActivityDesigner Parallel
 Il **parallela** ActivityDesigner è reperibile nel **flusso di controllo** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti**scheda sul lato sinistro del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **parallelo** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie ovunque attività vengono in genere posizionate, ad esempio, all'interno di un **Sequenza** ActivityDesigner. Dopo averlo rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], viene creato un <xref:System.Activities.Statements.Parallel> attività, che per impostazione predefinita contiene un <xref:System.Activities.Activity.DisplayName%2A> di **parallela**

 Per aggiungere un'attività per il <xref:System.Activities.Statements.Parallel.Branches%2A> raccolta dell'attività parallel, trascinare un altro ActivityDesigner dal **della casella degli strumenti** e rilasciarla sul triangolo all'interno di **parallela** ActivityDesigner. I triangoli si trovano di fianco alle attività contenute nei rami. È possibile aggiungere ulteriori attività ripetendo questa procedura. Le attività possono essere riordinate trascinandoli e rilasciandoli all'interno di **parallela** ActivityDesigner.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Proprietà di ParallelActivity in Progettazione flussi di lavoro
 Nella tabella seguente sono elencate le proprietà dell'attività Parallel e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è **parallela**. Il valore può essere modificato facoltativamente nel **proprietà** griglia o direttamente nell'intestazione dell'ActivityDesigner.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contiene la raccolta di attività figlio da eseguire.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Restituisce il risultato dopo il completamento di un ramo. Se restituisce **True**, quindi pianificati in sospeso di rami vengono annullati. Se questa proprietà non è impostata o restituisce **False**, l'attività viene completata quando tutte le relative attività figlio sono stati completati. Il valore predefinito è **null**.|

## <a name="see-also"></a>Vedere anche

- [sequenza](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)