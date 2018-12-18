---
title: ActivityDesigner DoWhile | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d8edec0edcc8461c18d7a90df6a776c96436ae3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dowhile-activity-designer"></a>ActivityDesigner DoWhile
Il <xref:System.Activities.Statements.DoWhile> attività viene eseguita l'attività contenuta nel relativo <xref:System.Activities.Statements.DoWhile.Body%2A> almeno una volta, fino a che una condizione specificata restituisce **false**. Se è necessario non eseguire l'attività contenuta in un corpo del ciclo o eseguirla più volte, usare l'attività alternativa <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Proprietà di DoWhile in Progettazione flussi di lavoro
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.DoWhile> e ne viene descritto l'uso nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|L'attività da eseguire se la condizione è **true**. Per aggiungere il <xref:System.Activities.Statements.DoWhile.Body%2A> attività, trascinare un'attività dalla casella degli strumenti nel **corpo** casella il **DoWhile** ActivityDesigner con testo di suggerimento "Rilasciare l'attività".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Condizione da valutare prima di ogni iterazione del ciclo. Per impostare il <xref:System.Activities.Statements.DoWhile.Condition%2A>, digitare un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] espressione il **condizione** casella il **DoWhile** attività della finestra di progettazione o nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [While](../workflow-designer/while-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)