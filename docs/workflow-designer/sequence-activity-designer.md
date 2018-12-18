---
title: Sequenza di ActivityDesigner | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d27a6f75205efc11fca49ee309f59fce6332a77
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sequence-activity-designer"></a>ActivityDesigner Sequence
L'attività <xref:System.Activities.Statements.Sequence> contiene una raccolta ordinata di attività figlio eseguite nell'ordine.

 Un altro sistema per eseguire un set delle attività nell'ordine consiste nell'usare un'attività <xref:System.Activities.Statements.Flowchart>. È consigliabile utilizzare il [diagramma di flusso](../workflow-designer/flowchart-activity-designer.md) quando si dispone di una semplice creazione di un ramo o il flusso di programma che si desidera modellare illustra il metodo di ciclo.

## <a name="using-the-sequence-activity-designer"></a>Utilizzo dell'ActivityDesigner Sequence
 Per aggiungere un <xref:System.Activities.Statements.Sequence> attività, trascinare il **sequenza** ActivityDesigner dal **della casella degli strumenti** e rilasciarla sull'area di progettazione del flusso di lavoro di Windows. Per aggiungere un'attività figlio a questa <xref:System.Activities.Statements.Sequence> attività, trascinare un'altra attività dal **della casella degli strumenti** e rilasciarla sul triangolo nella casella con il testo di suggerimento "Rilasciare l'attività".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività della sequenza in Progettazione flussi di lavoro 
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Sequence> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Sequence> nell'intestazione. Il valore predefinito è Sequence. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedere anche

- [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)