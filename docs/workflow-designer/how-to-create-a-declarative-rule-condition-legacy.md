---
title: 'Procedura: creare una condizione della regola dichiarativa (Legacy) | Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e8b1d1220f11d27ee193e3e82168f4c10558d86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Procedura: creare una condizione della regola dichiarativa (legacy)
In questo argomento viene illustrato come dichiarare una condizione della regola con la progettazione del flusso di lavoro di Windows legacy che fa riferimento il [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Restituisce un'istruzione di condizione **True** o **False**. Una condizione della regola dichiarativa è un'istruzione di condizione che viene creata utilizzando il [finestra di dialogo Editor regole condizione (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e archiviati in formato XML con il flusso di lavoro. Può includere predicati che confrontano lo stato del flusso di lavoro con l'algebra booleana che combina più predicati.

 Le condizioni di regole dichiarative vengono usate nelle attività predefinite di Windows Workflow Foundation di seguito riportate:

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [Attività WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Per creare una condizione di regole dichiarative usando l’Editor della condizione della regola

1.  L'attività **proprietà** finestra, fare clic su di **condizione** proprietà o **UntilCondition** proprietà, a seconda dell'attività.

2.  Selezionare **condizione della regola dichiarativa** dall'elenco per la proprietà.

3.  Espandere il **condizione** o **UntilCondition** proprietà.

4.  Fare clic su di **ConditionName** proprietà.

5.  Fare clic su di **ConditionName** i puntini di sospensione **[…]**  per aprire la **Seleziona condizione** la finestra di dialogo.

6.  Fare clic su **nuova condizione** per aprire la **Editor condizione della regola** la finestra di dialogo.

7.  Digitare l'espressione per la condizione di **condizione** casella di testo.

     Per informazioni su come creare espressioni di condizione, vedere [finestra di dialogo Editor regole condizione (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8.  Dopo aver creato l'espressione della condizione, fare clic su **OK** per chiudere la finestra di dialogo e creare la condizione della regola con un nome assegnato.

     Il **Seleziona condizione** verrà visualizzata la finestra di dialogo.

     Per informazioni sull'utilizzo di **Seleziona condizione** la finestra di dialogo, vedere [selezionare la finestra di dialogo condizione (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Vedere anche

- [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)
- [Utilizzo di ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)
- [Utilizzo dell'attività IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)
- [Utilizzo dell'attività di replica](http://go.microsoft.com/fwlink?LinkID=65080)
- [Utilizzo di While attività](http://go.microsoft.com/fwlink?LinkID=65091)
- [Finestra di dialogo Editor condizione della regola (legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)
- [Finestra di dialogo Seleziona condizione (legacy)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [Utilizzo delle condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)