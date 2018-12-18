---
title: ActivityDesigner diagramma di flusso | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7db449f538f09a247bc3c67ee26f487a6c81eb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="flowchart-activity-designer"></a>ActivityDesigner Diagramma di flusso
L'attività <xref:System.Activities.Statements.Flowchart> viene usata per creare flussi di lavoro che definiscono e gestiscono controlli di flusso complessi. È possibile creare un'attività <xref:System.Activities.Statements.Flowchart> tramite codice o usando [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In questo argomento viene descritto come usare [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] a tale scopo. L'ActivityDesigner del flusso di lavoro di progettazione del flusso di lavoro di Windows consente agli sviluppatori di creare flussi di lavoro in modo naturale.

## <a name="the-flowchart-activity"></a>Attività Flowchart
 <xref:System.Activities.Statements.Flowchart> specifica un elemento <xref:System.Activities.Statements.Flowchart.StartNode%2A> univoco che viene eseguito all'avvio del flusso di lavoro e usa una rete di <xref:System.Activities.Statements.Flowchart.Nodes%2A> collegati per creare cicli arbitrari o per deviare in un determinato momento il flusso dell'esecuzione in un altro punto del flusso di lavoro.

### <a name="using-the-flowchart-activity-designer"></a>Utilizzo dell'ActivityDesigner Flowchart
 Il **diagramma di flusso** ActivityDesigner è reperibile nel **diagramma di flusso** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti**scheda la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu o CTRL + ALT + X.)

 Il **diagramma di flusso** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie ovunque vengono in genere posizionate le attività, come un'attività radice o come elemento figlio di un'altra attività del flusso di controllo. Se il **diagramma di flusso** ActivityDesigner viene rilasciato in uno spazio vuoto [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie di attacco, viene creato un <xref:System.Activities.Statements.Flowchart> attività, che per impostazione predefinita si presenta in una visualizzazione espansa in cui è il nodo iniziale che avvia l'esecuzione rappresentato come una palla di colore verde. Se il **diagramma di flusso** ActivityDesigner viene rilasciato in un'altra attività del flusso di controllo, si presenta come una visualizzazione ridotta a icona che può essere espansa facendo doppio clic su di **diagramma di flusso** ActivityDesigner. Tutte le attività di **della casella degli strumenti** possono essere trascinate direttamente il **diagramma di flusso** ActivityDesigner, insieme ad altre attività del flusso di controllo.

 Dopo aver rilasciato diversi ActivityDesigner nell'area di disegno di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], è possibile collegare tra loro gli oggetti <xref:System.Activities.Activity> che rappresentano per specificarne l'ordine di esecuzione. Per creare un collegamento tra un'attività di origine e un'attività di destinazione, spostare il mouse sulla finestra di progettazione dell'attività di origine in modo da visualizzare handle quadrati su ciascun lato. Fare clic su uno degli handle quadrati e, tenendo premuto il pulsante del mouse, trascinarlo su uno degli handle visualizzati in modo simile intorno all'attività di destinazione durante il passaggio del mouse. Dopo aver rilasciato il pulsante del mouse, verrà creato un collegamento tra queste due attività rappresentato da una freccia che collega la finestra di progettazione di origine a quella di destinazione.

### <a name="flowchart-activity-properties"></a>Proprietà dell'attività Flowchart
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Flowchart> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome visualizzato nell'intestazione dell'ActivityDesigner. Il valore predefinito è Flowchart. Il valore può essere modificato nel **proprietà** finestra o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Raccolta di variabili incluse nell'ambito di questa attività <xref:System.Activities.Statements.Flowchart> per condividere lo stato tra le relative attività figlio.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode> eseguito all'avvio di <xref:System.Activities.Statements.Flowchart>.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Contiene la raccolta di oggetti <xref:System.Activities.Statements.FlowNode> inclusi nell'attività <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Vedere anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)