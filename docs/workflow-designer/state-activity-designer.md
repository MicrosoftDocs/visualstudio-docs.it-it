---
title: ActivityDesigner Progettazione flussi di lavoro
description: Informazioni sull'attività StateMachine e su come usare l'ActivityDesigner State per aggiungere uno stato a un flusso di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: abf4e81ecd258668c93b674410f029e6be0f5bf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873515"
---
# <a name="state-activity-designer"></a>ActivityDesigner State

Un oggetto <xref:System.Activities.Statements.State> rappresenta uno stato in cui può trovarsi una macchina a stati.

## <a name="using-the-state-activity-designer"></a>Utilizzo della Finestra di progettazione di stato.

Per aggiungere un oggetto <xref:System.Activities.Statements.State> a un flusso di lavoro, trascinare l'ActivityDesigner **stato** dalla sezione **macchina a stati** della **casella degli strumenti** e rilasciarlo su un' <xref:System.Activities.Statements.StateMachine> attività nell'area di progettazione flussi di lavoro. Un'attività di <xref:System.Activities.Statements.State> può essere rilasciata in <xref:System.Activities.Statements.StateMachine> e le transizioni possono essere aggiunte successivamente, o una transizione può essere creata quando viene rilasciata un'attività di <xref:System.Activities.Statements.State>. Per aggiungere un' <xref:System.Activities.Statements.State> attività e creare una transizione in un passaggio, trascinare un'attività **stato** dalla sezione **macchina a stati** della **casella degli strumenti** e passarla su un altro stato nella finestra di progettazione del flusso di lavoro. Quando l'oggetto <xref:System.Activities.Statements.State> trascinato si trova su un altro oggetto <xref:System.Activities.Statements.State>, intorno a <xref:System.Activities.Statements.State> verranno visualizzati quattro triangoli. Se l'oggetto <xref:System.Activities.Statements.State> viene rilasciato su uno dei quattro triangoli, viene aggiunto alla macchina a stati e una transizione viene creata dall'oggetto <xref:System.Activities.Statements.State> di origine all'oggetto <xref:System.Activities.Statements.State> di destinazione rilasciato. Per ulteriori informazioni, vedere la pagina relativa alla [transizione](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di stato in Progettazione flussi di lavoro 

Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.State> che possono essere impostate usando la finestra di progettazione flussi di lavoro e viene descritta la modalità di utilizzo nella finestra di progettazione. Alcune di queste proprietà possono essere modificate nella griglia delle proprietà, mentre altre possono essere modificate nell'area di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.State> nell'intestazione. Il valore predefinito è **state**. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner. <xref:System.Activities.Statements.State.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Statements.State.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.State.Entry%2A>|Falso|Specifica l'azione che si verifica quando viene eseguita la transizione di questo stato. Quando l' <xref:System.Activities.Statements.State> attività viene espansa, questo valore può essere impostato trascinando un'attività dalla **casella degli strumenti** e rilasciandola nella sezione **entry** dello stato.|
|<xref:System.Activities.Statements.State.Exit%2A>|Falso|Specifica l'azione che si verifica quando viene eseguita la transizione da questo stato. Quando l' <xref:System.Activities.Statements.State> attività viene espansa, questo valore può essere impostato trascinando un'attività dalla **casella degli strumenti** e rilasciandola nella sezione di **uscita** dello stato.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Falso|Vengono elencate le transizioni possibili originate da <xref:System.Activities.Statements.State>. Ogni elemento nell'elenco ha un collegamento a <xref:System.Activities.Statements.Transition> collegato e a <xref:System.Activities.Statements.State> di destinazione. Una volta fatto clic sul collegamento la finestra di progettazione passerà a una visualizzazione espansa di <xref:System.Activities.Statements.Transition> o di <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>Vedi anche

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transizione](../workflow-designer/transition-activity-designer.md)
