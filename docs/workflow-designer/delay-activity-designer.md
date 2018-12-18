---
title: Ritardo ActivityDesigner | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7159330588151d4845184fcb6688b20f8d13afd0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="delay-activity-designer"></a>ActivityDesigner Delay
Il **ritardo** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Delay> attività.

## <a name="the-delay-activity"></a>Attività Delay
 L'attività <xref:System.Activities.Statements.Delay> ritarda l'esecuzione di un flusso di lavoro per una quantità di tempo specificata.

### <a name="using-the-delay-activity-designer"></a>Utilizzo dell'ActivityDesigner Delay
 Il **ritardo** ActivityDesigner è reperibile nel **primitive** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti**scheda della finestra il [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **ritardo** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.Delay> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito Delay. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **ritardo** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-delay-properties"></a>Proprietà di Delay
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Delay> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Delay>. Il valore predefinito è Delay. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Durata del ritardo del flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà. Per specificare tale durata, digitare un valore <xref:System.TimeSpan> letterale nel formato 00:00:00 o un'espressione Visual Basic.|

## <a name="see-also"></a>Vedere anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [assegnare](../workflow-designer/assign-activity-designer.md)
- [Activity Designer Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)