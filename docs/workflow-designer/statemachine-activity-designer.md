---
title: ActivityDesigner StateMachine | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: "5"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 1800bfc9e60d52ea5c06bb94fdb765348a977681
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="statemachine-activity-designer"></a>ActivityDesigner StateMachine
L'attività <xref:System.Activities.Statements.StateMachine> contiene una raccolta di stati e modella i flussi di lavoro usando il paradigma comune della macchina a stati.  
  
## <a name="using-the-statemachine-activity-designer"></a>Utilizzo dell'ActivityDesigner StateMachine  
 Per aggiungere un <xref:System.Activities.Statements.StateMachine> attività, trascinare il **StateMachine** ActivityDesigner dal **macchina a stati** sezione il **della casella degli strumenti** e rilasciarlo sul [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] area. Per aggiungere uno stato figlio a questa <xref:System.Activities.Statements.StateMachine> attività, trascinare un <xref:System.Activities.Statements.State> o <xref:System.Activities.Core.Presentation.FinalState> dal **della casella degli strumenti** e rilasciarla il **StateMachine**.  
  
### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività StateMachine in Progettazione flussi di lavoro  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.StateMachine> che possono essere impostate usando la finestra di progettazione flussi di lavoro e viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia della proprietà e alcune nell'area della finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.StateMachine> nell'intestazione. Il valore predefinito è **StateMachine**. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner. <xref:System.Activities.Activity.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)