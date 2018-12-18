---
title: 'Procedura: creare un Set di regole di PolicyActivity (Legacy) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 1b57fe5f33bdbc4dfb7ab76856bdd80a3246ea9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Procedura: creare un set di regole per l'attività PolicyActivity (legacy)
In questo argomento viene descritto come creare un set di regole per PolicyActivity usando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Dopo avere trascinato un **criteri** elemento attività dal **della casella degli strumenti** all'area di progettazione del flusso di lavoro, è possibile selezionare una regola esistente o creare una nuovo set di regole per il [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) attività. Si seleziona una regola impostata per l'utilizzo di [selezionare regola impostare la finestra di dialogo (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) e per creare set di regole, utilizzare il [la finestra di dialogo Editor Set regola (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  È possibile aprire il [la finestra di dialogo Editor Set regola (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) la finestra di dialogo direttamente facendo doppio clic su un [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) attività nell'area di progettazione del flusso di lavoro.  
  
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
 [Attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Finestra di dialogo Imposta selezionare regola (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Finestra di dialogo Editor (Legacy) del Set di regole](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Utilizzando l'attività dei criteri](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)