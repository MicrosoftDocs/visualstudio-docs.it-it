---
title: InvokeDelegate | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 93e41d98b156b6314158a1cc99e368092b0cf494
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="invokedelegate"></a>InvokeDelegate
Il **InvokeDelegate** designer viene utilizzato per creare e configurare un <xref:System.Activities.Statements.InvokeDelegate> attività.

## <a name="the-invokedelegate-activity"></a>L'attività InvokeDelegate
 L'oggetto <xref:System.Activities.Statements.InvokeDelegate> chiama un delegato pubblico.

### <a name="using-the-invokedelegate-activity-designer"></a>Utilizzo dell'ActivityDesigner InvokeDelegate
 Il **InvokeDelegate** ActivityDesigner è reperibile nel **primitive** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti** scheda [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **InvokeDelegate** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area in cui le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.InvokeDelegate> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito InvokeDelegate. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **InvokeDelegate** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-invokedelegate-properties"></a>Proprietà di InvokeDelegate
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeDelegate> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeDelegate>. Il valore predefinito è InvokeDelegate.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nome dell'elemento <xref:System.Activities.ActivityDelegate> da richiamare quando viene eseguita l'attività. È possibile modificare questa proprietà nell'area della finestra di progettazione. Si tratta di una proprietà obbligatoria.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Raccolta dell'argomento del delegato chiamato. Le chiavi sono i nomi degli oggetti parametro nel <xref:System.Activities.ActivityDelegate> e i valori sono gli argomenti le cui espressioni vengono valutate ed assegnate agli oggetti parametro corrispondente. Nella griglia delle proprietà, fare clic sul pulsante con puntini di sospensione di **DelegateArguments** campo, viene visualizzato il **DelegateArguments** finestra di dialogo che consente di impostare questa proprietà. Fare clic su di **Crea argomento** campo per aggiungere gli argomenti.|

## <a name="see-also"></a>Vedere anche

- [Procedura: Definire e usare delegati di attività in Progettazione del flusso di lavoro](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)