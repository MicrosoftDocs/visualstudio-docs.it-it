---
title: 'Procedura: creare progetti flusso di lavoro (Legacy) | Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca6fdbbd8a744c472c06fdefbdafce77679ec2c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-workflow-projects-legacy"></a>Procedura: creare progetti di flusso di lavoro (legacy)
Seguire questi passaggi per creare un progetto [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che viene destinato a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o a [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]. Questa procedura viene utilizzata la finestra di progettazione del flusso di lavoro Windows legacy fornita da [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

### <a name="to-create-a-workflow-project"></a>Creazione di un Progetto di flusso di lavoro 

1.  Avviare [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)].

2.  Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3.  Selezionare il **.NET Framework 3.0** opzione o **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] è **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e non usa la finestra di progettazione legacy.

4.  Nel **tipi di progetto** riquadro, selezionare progetti Visual c# o Visual Basic (progetti), quindi **flusso di lavoro**.

5.  Nel **modelli** riquadro, selezionare uno dei modelli di progetto installati:

    -   Applicazione console del flusso di lavoro sequenziale

    -   Libreria del flusso di lavoro sequenziale

    -   Libreria delle attività del flusso di lavoro

    -   Applicazione console del flusso di lavoro della macchina a stati

    -   Libreria del flusso di lavoro di una macchina a stati

    -   Progetto del flusso di lavoro vuoto

6.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.

7.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare alla directory.

     Se si desidera una directory della soluzione creata per il progetto, selezionare il **Crea directory per soluzione** casella di controllo e immettere un nome per il **Nome soluzione** casella.

8.  Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)