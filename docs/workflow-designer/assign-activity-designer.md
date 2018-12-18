---
title: ActivityDesigner ASSIGN | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e5992420bb83323525e0b36bbc7d3b383ca9a3a2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="assign-activity-designer"></a>ActivityDesigner Assign
Il **assegnare** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Assign> attività.

## <a name="the-assign-activity"></a>Attività Assign
 L'attività <xref:System.Activities.Statements.Assign> assegna un valore a una variabile o a un argomento.

### <a name="using-the-assign-activity-designer"></a>Utilizzo dell'ActivityDesigner Assign
 Il **assegnare** ActivityDesigner è reperibile nel **primitive** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti**scheda (in alternativa, selezionare **della casella degli strumenti** dal **vista** menu o CTRL + ALT + X.)

 Il **assegnare** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area in cui le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Crea un <xref:System.Activities.Statements.Assign> attività con valore predefinito è **DisplayName** ASSIGN. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **assegnare** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-assign-properties"></a>Proprietà di Assign
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Assign> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Assign>. L'impostazione predefinita è Assign. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|La variabile o l'argomento cui è assegnata la proprietà <xref:System.Activities.Statements.Assign.Value%2A>. È necessario che sia un identificativo valido di Visual Basic. Per impostare la proprietà, digitare un'espressione Visual Basic nel **a** casella il **assegnare** attività della finestra di progettazione o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valore assegnato alla variabile. Per impostare il <xref:System.Activities.Statements.Assign.Value%2A>, digitare un'espressione Visual Basic nel **valore** casella il **assegnare** attività della finestra di progettazione o nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [ritardo](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)