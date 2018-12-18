---
title: ActivityDesigner CompensableActivity | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8f9fcf62b727ef3c8b607b503b3305508921e30
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="compensableactivity-activity-designer"></a>ActivityDesigner CompensableActivity
Il **CompensableActivity** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.CompensableActivity> attività.

## <a name="the-compensableactivity-activity"></a>Attività CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> definisce un'unità di lavoro che può essere confermata o compensata dopo l'esito positivo del completamento.

### <a name="using-the-compensableactivity-activity-designer"></a>Utilizzo dell'ActivityDesigner CompensableActivity
 Il **CompensableActivity** ActivityDesigner è reperibile nel **transazione** categoria del **della casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**  scheda sul lato sinistro del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **CompensableActivity** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.CompensableActivity> con un elemento <xref:System.Activities.Activity.DisplayName%2A> predefinito di CompensableActivity. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **CompensableActivity** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-compensableactivity-properties"></a>Proprietà di CompensableActivity
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CompensableActivity> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. È possibile modificare le proprietà <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Activity%601.Result%2A> nella griglia delle proprietà ma le altre proprietà devono essere modificate nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CompensableActivity>. Il valore predefinito è CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Specifica il valore restituito di <xref:System.Activities.Statements.CompensableActivity>. Questa proprietà deve essere modificata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di compensazione, di annullamento e di conferma. Per aggiungere il <xref:System.Activities.Statements.CompensableActivity.Body%2A> attività, trascinare un'attività dal **della casella degli strumenti** nel **corpo** casella il **CompensableActivity** ActivityDesigner con testo di suggerimento "Drop attività".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Specifica l'attività eseguita in caso di annullamento. Per aggiungere l'attività, eliminare la finestra di progettazione dal **della casella degli strumenti** nel **CancellationHandler** casella il **CompensableActivity** ActivityDesigner con testo di suggerimento "Drop Attività".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Specifica l'attività da eseguire quando si esegue la compensazione per l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Compensate>.<br /><br /> Per aggiungere l'attività, rilasciarne la finestra di progettazione dal **della casella degli strumenti** nel **CompensationHandler** casella il **CompensableActivity** ActivityDesigner con testo di suggerimento " Rilasciare l'attività".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Specifica l'attività da eseguire quando si conferma l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Confirm>.<br /><br /> Per aggiungere l'attività, rilasciarne la finestra di progettazione dal **della casella degli strumenti** nel **ConfirmationHandler** casella il **CompensableActivity** ActivityDesigner con testo di suggerimento " Rilasciare l'attività".|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Conferma](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)