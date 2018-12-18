---
title: 'Procedura: creare una libreria | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: "12"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: e2dc5245dd50fd2a5211d55107e537fbc8eb6eb8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-activity-library"></a>Procedura: creare una libreria attività
Le attività personalizzate sono usate per modellare i processi aziendali particolari in un flusso di lavoro. Il modello Libreria attività in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] è stato fornito per consentire di creare tali attività personalizzate usando visivamente [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
### <a name="to-create-a-workflow-activity-library"></a>Per creare una libreria attività flussi di lavoro  
  
1.  Avviare [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Nel **File** dal menu **New**, quindi selezionare **progetto...** .  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3.  Nel **tipi di progetto** riquadro, selezionare **flusso di lavoro** da uno di **Visual c#** progetti o **Visual Basic** raggruppamenti in base il preferenze della lingua.  
  
4.  Nel **modelli** riquadro, selezionare **libreria attività**.  
  
5.  Nel **nome** casella, digitare un nome descrittivo per il progetto per renderlo facilmente identificabile.  
  
6.  Nel **percorso** casella, digitare la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.  
  
7.  Nel **soluzione** casella, digitare un nome descrittivo per la soluzione, quindi fare clic su **OK**.  
  
    > [!NOTE]
    >  Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], fare clic con il pulsante destro la soluzione in **Esplora**e selezionare **Aggiungi**, quindi  **Nuovo progetto...**  per aprire la **nuovo progetto** la finestra di dialogo. Procedere come descritto sopra in questa procedura.  
  
8.  Il modello di progetto crea una definizione di attività in XAML. [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] verrà visualizzato con l'area di disegno per l'attività personalizzata.  
  
9. Trascinare un'attività dal **della casella degli strumenti** all'area di progettazione per includerla nell'attività personalizzata.  
  
    > [!CAUTION]
    >  È consentita una sola attività figlio nel corpo dell'attività personalizzata. L'attività in questione può tuttavia essere un oggetto CompositeActivity, quale <xref:System.Activities.Statements.Sequence> o <xref:System.Activities.Statements.Flowchart>.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un'attività](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)   
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)