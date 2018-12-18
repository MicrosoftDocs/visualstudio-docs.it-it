---
title: ActivityDesigner Pick | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c9528d46d43441333723ba67f324ca46929eb38
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="pick-activity-designer"></a>ActivityDesigner Pick
Nell'attività <xref:System.Activities.Statements.Pick> è disponibile il flusso di controllo basato sugli eventi. L'attività esegue uno di diversi rami in risposta a un evento di attivazione.

## <a name="the-pick-activity"></a>Attività Pick
 Un'attività <xref:System.Activities.Statements.Pick> contiene una raccolta di oggetti <xref:System.Activities.Statements.PickBranch>, uno dei quali può essere eseguito dall'attività <xref:System.Activities.Statements.Pick> per effetto di un evento in entrata che funge da trigger. In questo modo Progettazione flussi di lavoro di Windows fornisce modellazione del flusso di controllo basato su eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>. All'inizio di un <xref:System.Activities.Statements.Pick> esecuzione dell'attività, tutte le attività del trigger del <xref:System.Activities.Statements.PickBranch> elementi pianificati. Quando la prima attività viene completata, l'attività dell'azione corrispondente è pianificata e tutte le altre attività del trigger sono annullate.

### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick
 Il **Pick** ActivityDesigner è reperibile nel **flusso di controllo** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti**scheda [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu o CTRL + ALT + X.)

 Il **selezionare** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie ovunque sono in genere posizionate le attività, ad esempio all'interno di un  **Sequenza** ActivityDesigner. Dopo averlo rilasciato in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], viene creata un'attività <xref:System.Activities.Statements.Pick> che per impostazione predefinita contiene due attività <xref:System.Activities.Statements.PickBranch> vuote come elementi i cui nomi visualizzati sono Branch1 e Branch2. I rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> i valori delle proprietà possono essere modificati nella **PickBranch** intestazione ActivityDesigner o all'interno di **proprietà** finestra per ogni ramo.

 Esistono due modi per aggiungere <xref:System.Activities.Statements.PickBranch> attività alla raccolta di un <xref:System.Activities.Statements.Pick> oggetto: trascinando e rilasciando il **PickBranch** dalla finestra di progettazione di **della casella degli strumenti** o utilizzando il menu di scelta rapida da all'interno di **Pick** area di progettazione. Per informazioni dettagliate, vedere il [PickBranch](../workflow-designer/pickbranch-activity-designer.md) argomento. Si noti che l'unico elemento che possono essere inserito all'interno di un **Pick** ActivityDesigner è un **PickBranch** ActivityDesigner.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di prelievo in Progettazione flussi di lavoro
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Pick> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Pick> nell'intestazione. Il valore predefinito è Pick. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [Attività di selezione](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso dell'attività Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)