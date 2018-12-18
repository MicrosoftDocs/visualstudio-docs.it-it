---
title: 'Procedura: creare una libreria di attività del flusso di lavoro (Legacy) | Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18fa570f732f71336ce5a2f5e8e56d1185366afa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Procedura: creare una libreria di attività del flusso di lavoro (legacy)

Seguire questi passaggi per creare un progetto libreria di attività del flusso di lavoro usando la finestra di progettazione del flusso di lavoro Windows legacy fornita da [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

### <a name="to-create-a-workflow-activity-library-project"></a>Per creare un progetto di raccolta di attività del flusso di lavoro

1.  Avviare Visual Studio.

2.  Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3.  Selezionare il **.NET Framework 3.0** opzione o **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] è **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e non usa la finestra di progettazione legacy.

4.  Nel **tipi di progetto** riquadro, selezionare Visual c# o Visual Basic (sotto **altri linguaggi**) e quindi selezionare **flusso di lavoro**.

5.  Nel **modelli** riquadro, selezionare **Workflow Activity Library**.

6.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.

7.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.

     Se si desidera una directory della soluzione creata per il progetto, selezionare il **Crea directory per soluzione** casella di controllo e immettere un nome per il **Nome soluzione** casella.

8.  Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Uso dell'Activity Designer legacy](../workflow-designer/using-the-legacy-activity-designer.md)
- [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)
- [Lo sviluppo di attività del flusso di lavoro](http://msdn.microsoft.com/en-us/19876dfc-dfa5-4d52-b1f5-1d087474cc52)
- [Attività di Windows Workflow Foundation](http://msdn.microsoft.com/en-us/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)