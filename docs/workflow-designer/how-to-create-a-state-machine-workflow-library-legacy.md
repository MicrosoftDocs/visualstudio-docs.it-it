---
title: 'Procedura: creare una libreria del flusso di lavoro macchina a stati (Legacy) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 73fe219a3047758f66dbff47e59031adb1de9258
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Procedura: creare una libreria del flusso di lavoro di macchina a stati (legacy)
Seguire questi passaggi per creare un progetto libreria flusso di lavoro di una macchina a stati usando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy fornita da [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-a-state-machine-workflow-library-project"></a>Procedura: creazione di un progetto di libreria del flusso di lavoro di una macchina a stati   
  
1.  Avviare Visual Studio.  
  
2.  Nel **File** dal menu **New**, quindi selezionare **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3.  Selezionare il **.NET Framework 3.0** opzione o **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere alla finestra di progettazione legacy.  
  
    > [!NOTE]
    >  L'opzione predefinita [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] è **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e non usa la finestra di progettazione legacy.  
  
4.  Nel **tipi di progetto** riquadro, selezionare Visual c# o Visual Basic (sotto **altri linguaggi**) e quindi selezionare **flusso di lavoro**.  
  
5.  Nel **modelli** riquadro, selezionare **libreria del flusso di lavoro macchina a stati**.  
  
6.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.  
  
7.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.  
  
     Se si desidera una directory della soluzione creata per il progetto, selezionare il **Crea directory per soluzione** casella di controllo e immettere un nome per il **Nome soluzione** casella.  
  
8.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di progetti di flusso di lavoro Legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Flussi di lavoro della macchina a stati](/dotnet/framework/windows-workflow-foundation/state-machine-workflows)