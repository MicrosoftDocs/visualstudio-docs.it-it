---
title: 'Procedura: creare una libreria del flusso di lavoro macchina a stati (Legacy) | Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8220c6e9dbd2d97e0bf1017498ca3b295424863
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Procedura: creare una libreria del flusso di lavoro di macchina a stati (legacy)

Seguire questi passaggi per creare un progetto di libreria del flusso di lavoro macchina a stati usando la finestra di progettazione del flusso di lavoro Windows legacy fornita da [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

### <a name="to-create-a-state-machine-workflow-library-project"></a>Procedura: creazione di un progetto di libreria del flusso di lavoro di una macchina a stati 

1.  Avviare Visual Studio.

2.  Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3.  Selezionare il **.NET Framework 3.0** opzione o **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] è **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e non usa la finestra di progettazione legacy.

4.  Nel **tipi di progetto** riquadro, selezionare Visual c# o Visual Basic (sotto **altri linguaggi**) e quindi selezionare **flusso di lavoro**.

5.  Nel **modelli** riquadro, selezionare **libreria del flusso di lavoro macchina a stati**.

6.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.

7.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.

     Se si desidera una directory della soluzione creata per il progetto, selezionare il **Crea directory per soluzione** casella di controllo e immettere un nome per il **Nome soluzione** casella.

8.  Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Flussi di lavoro della macchina a stati](/dotnet/framework/windows-workflow-foundation/state-machine-workflows)