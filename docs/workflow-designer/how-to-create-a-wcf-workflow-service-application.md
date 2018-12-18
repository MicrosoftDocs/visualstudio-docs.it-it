---
title: 'Procedura: creare un''applicazione di servizio del flusso di lavoro WCF | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 8730b8f1611694ec7927b52fa4118cf3ca3801b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Procedura: creare un'applicazione del servizio flusso di lavoro WCF
Le applicazioni di servizi flusso di lavoro di [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] sono servizi di comunicazioni distribuite che scambiano messaggi con i client oltre i limiti dei processi. L'implementazione del contratto di servizio sul lato servizio viene eseguita in modo dichiarativo tramite le attività del flusso di lavoro [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] in modo analogo ai servizi flusso di lavoro legacy di .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>Per creare un'applicazione di servizi flusso di lavoro WCF  
  
1.  Avviare [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Nel **File** dal menu **New**, quindi selezionare **progetto...** .  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3.  Nel **modelli installati** riquadro, selezionare **WCF** o **flusso di lavoro** da uno di **Visual c#** o **diVisualBasic** a seconda del linguaggio scelto.  
  
4.  Nel riquadro centrale, selezionare **applicazione del servizio del flusso di lavoro WCF**.  
  
5.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.  
  
6.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.  
  
7.  Nel **soluzione** casella, selezionare questa opzione per creare una nuova soluzione e quindi fare clic su **OK**.  
  
    > [!NOTE]
    >  Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], fare clic con il pulsante destro la soluzione in **Esplora**e selezionare **Aggiungi**, quindi  **Nuovo progetto...**  per aprire la **nuovo progetto** la finestra di dialogo. Procedere come descritto sopra in questa procedura.  
  
8.  Il modello di progetto crea una definizione di servizio come XAML. [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] viene aperto sulla visualizzazione Progettazione con un'attività <xref:System.Activities.Statements.Sequence> che contiene un set di attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un'attività](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)   
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)