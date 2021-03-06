---
title: ActivityDesigner Progettazione flussi di lavoro Sequence
description: Informazioni sul modo in cui l'attività Sequence contiene una raccolta ordinata di attività figlio eseguite nell'ordine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c7bfc8c850cee9273af2af3b28f71b9d27209d9a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943640"
---
# <a name="sequence-activity-designer"></a>ActivityDesigner Sequence

L'attività <xref:System.Activities.Statements.Sequence> contiene una raccolta ordinata di attività figlio eseguite nell'ordine.

Un altro sistema per eseguire un set delle attività nell'ordine consiste nell'usare un'attività <xref:System.Activities.Statements.Flowchart>. Si consiglia di utilizzare il [diagramma](../workflow-designer/flowchart-activity-designer.md) di flusso quando si dispone di un semplice flusso del programma di diramazione o ciclo che si desidera modellare graficamente.

## <a name="using-the-sequence-activity-designer"></a>Utilizzo dell'ActivityDesigner Sequence

Per aggiungere un' <xref:System.Activities.Statements.Sequence> attività, trascinare l'ActivityDesigner **Sequence** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro. Per aggiungere un'attività figlio a questa <xref:System.Activities.Statements.Sequence> attività, trascinare un'altra attività dalla **casella degli strumenti** e rilasciarla sul triangolo nella casella con il testo del suggerimento "rilasciare l'attività".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività della sequenza in Progettazione flussi di lavoro 

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Sequence> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Sequence> nell'intestazione. Il valore predefinito è Sequence. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedi anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)