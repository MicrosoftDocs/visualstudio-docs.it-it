---
title: 'Procedura: creare un Set di regole di PolicyActivity (Legacy) | Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4911912aa46f5dc8a6aea9b9b20e87c1f83e576f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Procedura: creare un set di regole per l'attività PolicyActivity (legacy)

In questo argomento viene descritto come creare un set di regole impostato utilizzando la progettazione del flusso di lavoro di Windows legacy che fa riferimento il [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Dopo avere trascinato un **criteri** elemento attività dal **della casella degli strumenti** all'area di progettazione del flusso di lavoro, è possibile selezionare una regola esistente o creare una nuovo set di regole per il [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) attività. Si seleziona una regola impostata per l'utilizzo di [selezionare regola impostare la finestra di dialogo (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) e per creare set di regole, utilizzare il [la finestra di dialogo Editor Set regola (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> È possibile aprire il [la finestra di dialogo Editor Set regola (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) la finestra di dialogo direttamente facendo doppio clic su un [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) attività nell'area di progettazione del flusso di lavoro.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Per selezionare o creare un insieme di regole per un'attività di Policy

1.  Fare doppio clic sul [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), quindi fare clic su **proprietà** per aprire la **proprietà** finestra.

2.  Fare clic su di **RuleSetReference** proprietà.

3.  Eseguire una delle operazioni seguenti:

    -   Fare clic su di **RuleSetReference** i puntini di sospensione **[…]** , quindi selezionare una regola esistente di cui il [selezionare regola impostare la finestra di dialogo (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Andare al passaggio 10.

         -oppure-

    -   Digitare il nome da assegnare al set di regole. Fare clic su di **RuleSetReference** i puntini di sospensione **[…]** , quindi selezionare **modifica** nel [selezionare regola impostare la finestra di dialogo (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         oppure

    -   Digitare il nome da assegnare al set di regole. Espandere il **RuleSetReference** proprietà e selezionare i puntini di sospensione **[…]**  nel **RuleSet Definition** proprietà.

         Il [la finestra di dialogo Editor Set regola (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) apre.

4.  Nel [la finestra di dialogo Editor Set regola (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), fare clic su **Aggiungi regola** per aggiungere una nuova regola per il set di regole.

5.  Immettere il **nome**, **priorità**, e **rivalutazione** , proprietà o mantenere i valori predefiniti.

6.  Immettere il testo per il **condizione**.

7.  Immettere il testo per il **azioni Then** e **azioni Else**.

8.  Fare clic su **Aggiungi regola** per aggiungere un'altra regola.

9. Al termine, fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [Finestra di dialogo Seleziona set di regole (legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [Finestra di dialogo Editor set di regole (legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)
- [Utilizzando l'attività dei criteri](http://go.microsoft.com/fwlink?LinkID=65004)
- [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)