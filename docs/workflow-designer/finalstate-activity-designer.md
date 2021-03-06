---
title: ActivityDesigner Progettazione flussi di lavoro-FinalState
description: Informazioni su come usare FinalState designer per creare uno stato che termina un'istanza della macchina a Stati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a6ec51d17453a13f8c3ab1adffc5447afb5db7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894179"
---
# <a name="finalstate-activity-designer"></a>ActivityDesigner FinalState

La finestra di progettazione di <xref:System.Activities.Core.Presentation.FinalState> viene usata per creare un <xref:System.Activities.Statements.State> che termina un'istanza della macchina a stati.

## <a name="using-the-finalstate-activity-designer"></a>Uso di ActivityDesigner FinalState

**FinalState** Designer viene usato per creare un <xref:System.Activities.Statements.State> preconfigurato come stato di terminazione in una macchina a Stati. La proprietà di un oggetto <xref:System.Activities.Statements.State> creato con l'ActivityDesigner <xref:System.Activities.Core.Presentation.FinalState> è <xref:System.Activities.Statements.State.IsFinal%2A> impostata su **true**, non dispone di alcuna <xref:System.Activities.Statements.State.Exit%2A> attività e non ha origine alcuna transizione. Per utilizzare l'ActivityDesigner <xref:System.Activities.Core.Presentation.FinalState> per aggiungere un' <xref:System.Activities.Statements.State> attività preconfigurata come stato di terminazione in una macchina a Stati, trascinare l'ActivityDesigner **FinalState** dalla sezione **macchina a stati** della **casella degli strumenti** e rilasciarlo nella finestra di progettazione del flusso di lavoro. Un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState> può essere rilasciato in <xref:System.Activities.Statements.StateMachine> e le transizioni possono essere aggiunte successivamente, o una transizione può essere creata quando viene rilasciato un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState>. Per ulteriori informazioni sulla creazione di transizioni, vedere la pagina relativa alla [transizione](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di stato in Progettazione flussi di lavoro 

Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Core.Presentation.FinalState> che possono essere impostate usando la finestra di progettazione e viene descritta la modalità di utilizzo nella finestra di progettazione. Alcune di queste proprietà possono essere modificate nella griglia delle proprietà, mentre altre possono essere modificate nell'area di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.State> nell'intestazione. Il valore predefinito è **state**. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner. <xref:System.Activities.Statements.State.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Statements.State.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.State.Entry%2A>|Falso|Specifica l'azione che si verifica quando viene eseguita la transizione di questo stato. Questo valore può essere impostato trascinando un'attività dalla **casella degli strumenti** e rilasciandola nella <xref:System.Activities.Statements.State.Entry%2A> sezione dello stato.|

## <a name="see-also"></a>Vedi anche

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
- [Transizione](../workflow-designer/transition-activity-designer.md)