---
title: Se ActivityDesigner | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 950bff10372c9c40e047f891049e7cc387c8efc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="if-activity-designer"></a>ActivityDesigner If
L'attività <xref:System.Activities.Statements.If> valuta una condizione ed esegue un'attività che dipende dai risultati di tale valutazione. Questa attività è molto utile in caso di utilizzo di un stile di modellazione procedurale della programmazione. Un'attività <xref:System.Activities.Statements.If> può essere ad esempio annidata in un'attività <xref:System.Activities.Statements.Sequence> o in un'attività <xref:System.Activities.Statements.Parallel>. Se si usa un'attività <xref:System.Activities.Statements.Flowchart>, si prenda in considerazione l'uso alternativo di un'attività <xref:System.Activities.Statements.FlowDecision>.  
  
## <a name="if-properties-in-the-workflow-designer"></a>Proprietà di If in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.If> e ne viene descritto l'uso nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|La condizione che determina l'attività figlio da eseguire. Per impostare il <xref:System.Activities.Statements.If.Condition%2A>, digitare un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] espressione il **condizione** casella il **se** attività della finestra di progettazione o nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|L'attività da eseguire se il <xref:System.Activities.Statements.If.Condition%2A> è **false**. Per aggiungere un'attività che viene eseguita tramite il <xref:System.Activities.Statements.If.Else%2A> branching, rilasciarla dal **della casella degli strumenti** nel **Else** casella il **se** ActivityDesigner con testo di suggerimento " Rilasciare l'attività".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|L'attività da eseguire se il <xref:System.Activities.Statements.If.Condition%2A> è **true**. Per aggiungere un'attività che viene eseguita tramite il <xref:System.Activities.Statements.If.Then%2A> branching, rilasciarla dal **della casella degli strumenti** nel **quindi** casella il **se** ActivityDesigner con testo di suggerimento " Rilasciare l'attività".|  
  
## <a name="see-also"></a>Vedere anche  
 [Sequenza](../workflow-designer/sequence-activity-designer.md)   
 [Parallelo](../workflow-designer/parallel-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)