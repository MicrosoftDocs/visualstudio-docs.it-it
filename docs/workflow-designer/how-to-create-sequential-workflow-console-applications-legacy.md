---
title: 'Procedura: creare applicazioni Console flusso di lavoro sequenziale (Legacy) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 79969572e4cab24e93a6c593a23369a00243ae0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Procedura: creare applicazioni console del flusso di lavoro sequenziale (legacy)
Seguire questi passaggi per creare un progetto Applicazione console flusso di lavoro sequenziale usando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy fornita da [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>Creazione delle Applicazioni console del flusso di lavoro sequenziale  
  
1.  Avviare Visual Studio.  
  
2.  Nel **File** dal menu **New**, quindi selezionare **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3.  Selezionare il **.NET Framework 3.0** opzione o **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere alla finestra di progettazione legacy.  
  
    > [!NOTE]
    >  L'opzione predefinita [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] è **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e non usa la finestra di progettazione legacy.  
  
4.  Nel **tipi di progetto** riquadro, selezionare progetti Visual c# o progetti di Visual Basic (sotto **altri linguaggi**), quindi selezionare **flusso di lavoro**.  
  
5.  Nel **modelli** riquadro, selezionare **applicazione Console flusso di lavoro sequenziale**.  
  
6.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.  
  
7.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.  
  
     Verrà aperta la finestra di progettazione Windows Forms nella quale verrà visualizzato il Form1 del progetto creato.  
  
8.  Fare clic su **OK**.  
  
     Verrà aperta la finestra di Progettazione flussi di lavoro e verrà visualizzata l'area di progettazione del flusso di lavoro sequenziale creato.  
  
9. Trascinare un'attività dal **della casella degli strumenti** all'area di progettazione nel **rilasciare l'attività** area designata.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di progetti di flusso di lavoro Legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Sviluppo di flussi di lavoro](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)