---
title: Sequenza di ActivityDesigner | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 5d0635839b9d875c5c519ec41c6dcfa6dc02fa2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sequence-activity-designer"></a>ActivityDesigner Sequence
L'attività <xref:System.Activities.Statements.Sequence> contiene una raccolta ordinata di attività figlio eseguite nell'ordine.  
  
 Un altro sistema per eseguire un set delle attività nell'ordine consiste nell'usare un'attività <xref:System.Activities.Statements.Flowchart>. È consigliabile utilizzare il [diagramma di flusso](../workflow-designer/flowchart-activity-designer.md) quando si dispone di una semplice creazione di un ramo o il flusso di programma che si desidera modellare illustra il metodo di ciclo.  
  
## <a name="using-the-sequence-activity-designer"></a>Utilizzo dell'ActivityDesigner Sequence  
 Per aggiungere un <xref:System.Activities.Statements.Sequence> attività, trascinare il **sequenza** ActivityDesigner dal **della casella degli strumenti** e rilasciarlo sul [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] area. Per aggiungere un'attività figlio a questa <xref:System.Activities.Statements.Sequence> attività, trascinare un'altra attività dal **della casella degli strumenti** e rilasciarla sul triangolo nella casella con il testo di suggerimento "Rilasciare l'attività".  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività della sequenza in Progettazione flussi di lavoro   
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Sequence> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Sequence> nell'intestazione. Il valore predefinito è Sequence. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)