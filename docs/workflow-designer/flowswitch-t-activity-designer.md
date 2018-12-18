---
title: FlowSwitch&lt;T&gt; ActivityDesigner | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb8c28f835fad4e70b213d13aaeb654780b72297
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch&lt;T&gt; ActivityDesigner
L'attività <xref:System.Activities.Statements.FlowSwitch%601> è un nodo condizionale che consente la creazione di rami per il flusso di controllo in base ai criteri di corrispondenza quando sono necessari più di due rami alternativi. Se la creazione di rami per il flusso richiede solo due percorsi, usare invece l'attività <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>FlowSwitch < T\> attività
 Il <xref:System.Activities.Statements.FlowSwitch%601> attività contiene un <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> che restituisce un valore di tipo *T* (specificato dal parametro generico) durante la valutazione. L'attività contiene inoltre un set di <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> che specifica un mapping univoco tra i possibili risultati di questa valutazione e un set di oggetti <xref:System.Activities.Statements.FlowNode>. Il <xref:System.Activities.Statements.FlowNode> eseguito è quello il cui oggetto di tipo *T* corrisponde al valore della valutata <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. È possibile fornire facoltativamente un case <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> se non è presente alcuna corrispondenza.

### <a name="using-the-flowswitcht-activity-designer"></a>Utilizzare FlowSwitch\<T > ActivityDesigner
 Il **FlowSwitch\<T >** ActivityDesigner, vedere il **diagramma di flusso** categoria del **della casella degli strumenti**, accessibile facendo clic di **Casella degli strumenti** scheda sul lato sinistro del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **FlowSwitch\<T >** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area all'interno di un **diagramma di flusso** finestra di progettazione. Utilizzare il **Seleziona tipi di** finestra che visualizza per specificare il tipo (associato nel codice il <xref:System.Activities.Statements.FlowSwitch%601> dal parametro generico) ottenuto dalla valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Questa procedura crea un <xref:System.Activities.Statements.FlowSwitch%601> attività con etichettata **commutatore** all'interno di <xref:System.Activities.Statements.Flowchart> attività. Il <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> possono essere digitati il **espressione** casella del **proprietà** dalla finestra in cui viene visualizzato il testo di suggerimento "Immettere un'espressione VB".

 Sposta il mouse sopra il **FlowSwitch\<T >** ActivityDesigner per causare l'handle quadrati usati per collegare <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> da visualizzare lungo i bordi. Dopo avere trascinato il **FlowSwitch < T\>**  ActivityDesigner e altri ActivityDesigner sul **diagramma di flusso**, <xref:System.Activities.Activity> oggetti che rappresentano sono pronti per essere collegati tra loro Per specificare l'ordine di esecuzione. Per creare uno del <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associato il <xref:System.Activities.Statements.FlowSwitch%601>, fare clic su uno degli handle quadrati dei case sul perimetro del **FlowSwitch < T\>**  e trascinarlo su uno dei quadratini di ridimensionamento (tenendo premuto il pulsante del mouse) che viene visualizzato in modo simile intorno all'attività di destinazione quando si posiziona il puntatore del mouse sulla finestra di progettazione. Rilasciare il pulsante del mouse e una freccia di **FlowSwitch < T\>**  alla finestra di progettazione di destinazione che rappresenta questo case viene visualizzato. Il valore predefinito per questo case viene visualizzato sulla freccia e può essere modificato nel **Case** casella della finestra il **proprietà** finestra.

### <a name="the-flowswitcht-properties"></a>FlowSwitch < T\> proprietà
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.FlowSwitch%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Specifica l'espressione valutata per identificare l'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> cui passare nel percorso di esecuzione.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Specifica un mapping univoco tra i possibili risultati ottenuti dalla valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> e un set di oggetti <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Specifica il mapping quando la valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> non corrisponde a uno dei valori contenuti nell'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Vedere anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)
- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)