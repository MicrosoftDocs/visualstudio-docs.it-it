---
title: ActivityDesigner ActivityDesigner CancellationScope t
description: Informazioni su come usare l'ActivityDesigner ActivityDesigner CancellationScope t in Progettazione flussi di lavoro per creare e configurare un'attività ActivityDesigner CancellationScope t.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ef415763a67232f79b269650abecfe6bcabe6bd2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937199"
---
# <a name="cancellationscope-activity-designer"></a>ActivityDesigner CancellationScope

L'ActivityDesigner **ActivityDesigner CancellationScope t** viene usato per creare e configurare un' <xref:System.Activities.Statements.CancellationScope> attività.

## <a name="the-cancellationscope-activity"></a>Attività CancellationScope

L'attività <xref:System.Activities.Statements.CancellationScope> consente di specificare un'attività per la relativa logica di esecuzione e di annullamento.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CancellationScope

L'ActivityDesigner **ActivityDesigner CancellationScope t** è disponibile nella categoria **transazione** della **casella degli strumenti**. Per aprire la **casella degli strumenti**, selezionare la scheda **casella degli strumenti** della progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

È possibile trascinare l'ActivityDesigner **ActivityDesigner CancellationScope t** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro ogni volta che vengono inserite le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner **ActivityDesigner CancellationScope t** , viene creata un' <xref:System.Activities.Statements.CancellationScope> attività con un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> di ActivityDesigner CancellationScope t. Modificare il <xref:System.Activities.Activity.DisplayName%2A> valore nell'intestazione dell'ActivityDesigner **ActivityDesigner CancellationScope t** . È anche possibile modificarlo nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-cancellationscope-properties"></a>Proprietà di CancellationScope

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di uso nella finestra di progettazione. La <xref:System.Activities.Activity.DisplayName%2A> proprietà può essere modificata nella griglia delle proprietà ma le altre proprietà devono essere modificate sull'area Progettazione flussi di lavoro.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. Il valore predefinito è CancellationScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Vero|Specifica l'attività per la quale viene fornita la logica di annullamento. Per aggiungere l' <xref:System.Activities.Statements.CancellationScope.Body%2A> attività, rilasciare un'attività dalla **casella degli strumenti** nella casella **corpo** dell'ActivityDesigner **ActivityDesigner CancellationScope t** . Aggiungere il testo del suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Vero|Specifica l'attività eseguita in caso di annullamento. Per aggiungere l' <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> attività, rilasciare un'attività dalla **casella degli strumenti** nella casella **CancellationHandler** nell'ActivityDesigner **ActivityDesigner CancellationScope t** . Aggiungere il testo del suggerimento "drop Activity here".|

## <a name="see-also"></a>Vedi anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Confermare](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
