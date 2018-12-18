---
title: ActivityDesigner CancellationScope | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3231d62d5c961e63fa2a72374d5a1adcf50288f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="cancellationscope-activity-designer"></a>ActivityDesigner CancellationScope
Il **CancellationScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.CancellationScope> attività.

## <a name="the-cancellationscope-activity"></a>Attività CancellationScope
 L'attività <xref:System.Activities.Statements.CancellationScope> consente di specificare un'attività per la relativa logica di esecuzione e di annullamento.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CancellationScope
 Il **CancellationScope** ActivityDesigner è reperibile nel **transazione** categoria del **della casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**  scheda della finestra il [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **CancellationScope** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.CancellationScope> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito CancellationScope. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **CancellationScope** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-cancellationscope-properties"></a>Proprietà di CancellationScope
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. È possibile modificare la proprietà <xref:System.Activities.Activity.DisplayName%2A> nella griglia delle proprietà ma le altre proprietà devono essere modificate nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. Il valore predefinito è CancellationScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di annullamento. Per aggiungere il <xref:System.Activities.Statements.CancellationScope.Body%2A> attività, trascinare un'attività dal **della casella degli strumenti** nel **corpo** casella il **CancellationScope** ActivityDesigner con testo di suggerimento "Drop Attività".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Specifica l'attività eseguita in caso di annullamento. Per aggiungere il <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> attività, trascinare un'attività dal **della casella degli strumenti** nel **CancellationHandler** casella il **CancellationScope** ActivityDesigner con hint testo "Rilasciare l'attività".|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Conferma](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)