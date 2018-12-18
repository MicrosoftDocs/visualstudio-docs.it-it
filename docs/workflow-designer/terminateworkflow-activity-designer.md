---
title: ActivityDesigner TerminateWorkflow | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 444ea597fd6c76c8312369afcbc497e640bace6f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="terminateworkflow-activity-designer"></a>ActivityDesigner TerminateWorkflow
Il **TerminateWorkflow** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.TerminateWorkflow> attività.

## <a name="the-terminateworkflow-activity"></a>Attività TerminateWorkflow
 L'attività <xref:System.Activities.Statements.TerminateWorkflow> termina l'esecuzione di un flusso di lavoro.

### <a name="using-the-terminateworkflow-activity-designer"></a>Utilizzo dell'ActivityDesigner TerminateWorkflow
 Il **TerminateWorkflow** ActivityDesigner è reperibile nel **Runtime** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti** scheda (in alternativa, selezionare **della casella degli strumenti** dal **vista** menu o CTRL + ALT + X.)

 Il **TerminateWorkflow** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Crea un <xref:System.Activities.Statements.TerminateWorkflow> attività con valore predefinito è **DisplayName** terminateworkflow. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **TerminateWorkflow** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-terminateworkflow-properties"></a>Proprietà di TerminateWorkflow
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TerminateWorkflow> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.TerminateWorkflow>. Il valore predefinito è TerminateWorkflow. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Eccezione da generare quando viene terminato il flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Motivo che spiega perché è stato terminato il flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [Rendere persistenti](../workflow-designer/persist-activity-designer.md)