---
title: 'Procedura: creare un''applicazione Console flusso di lavoro | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: "16"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: fcadbe113e92c761559161bdd8a7eba6e95937d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-workflow-console-application"></a>Procedura: creare un'applicazione console flusso di lavoro
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] consente di creare flussi di lavoro per l'esecuzione di processi di utenti o di sistema. [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fornisce l'area di progettazione per la creazione di tali flussi. La [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] può essere usata per creare flussi di lavoro dall'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o può essere integrata in altre applicazioni che riallocano la finestra di progettazione.  
  
 In questo argomento viene descritto come usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] per creare un flusso di lavoro in un'applicazione console.  
  
### <a name="to-create-a-workflow-console-application"></a>Per creare un'applicazione console flusso di lavoro  
  
1.  Avviare [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Nel **File** dal menu **New**, quindi selezionare **progetto...** .  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3.  Nel **modelli installati** riquadro, selezionare **flusso di lavoro** da uno di **Visual c#** o **Visual Basic** raggruppamenti, a seconda del lingua di preferenza.  
  
4.  Nel riquadro centrale, selezionare **applicazione Console flusso di lavoro**.  
  
5.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.  
  
6.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.  
  
7.  Nel **soluzione** , immettere il nome per la nuova soluzione. Fare clic su **OK** per creare l'applicazione.  
  
    > [!NOTE]
    >  Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], fare clic con il pulsante destro la soluzione in **Esplora**e selezionare **Aggiungi**, quindi  **Nuovo progetto...**  per aprire la **nuovo progetto** la finestra di dialogo. Procedere come descritto sopra in questa procedura.  
  
8.  Il modello di progetto crea una definizione del flusso di lavoro in XAML mentre la definizione dell'applicazione console è in codice sorgente. In [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] verrà visualizzata l'area di disegno per il flusso di lavoro creato.  
  
9. Per creare un flusso di lavoro, trascinare attività o altri elementi del flusso di lavoro dal **della casella degli strumenti** all'area di progettazione del flusso di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)