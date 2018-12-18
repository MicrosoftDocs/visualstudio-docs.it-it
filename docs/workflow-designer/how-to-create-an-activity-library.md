---
title: 'Procedura: creare una libreria | Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: faa7c593d27474c0980e7c7df7bf932bd2d5431d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-activity-library"></a>Procedura: creare una libreria attività
Le attività personalizzate sono usate per modellare i processi aziendali particolari in un flusso di lavoro. Il modello libreria di attività in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] è stata specificata per consentire la creazione di tali attività personalizzate usando visivamente la finestra di progettazione del flusso di lavoro di Windows.

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
    > Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], fare clic con il pulsante destro la soluzione in **Esplora**e selezionare **Aggiungi**, quindi **Nuovo progetto...** per aprire la **nuovo progetto** la finestra di dialogo. Procedere come descritto sopra in questa procedura.

8.  Il modello di progetto crea una definizione di attività in XAML. Progettazione del flusso di lavoro di Windows viene visualizzato nell'area di lavoro per l'attività personalizzata.

9. Trascinare un'attività dal **della casella degli strumenti** all'area di progettazione per includerla nell'attività personalizzata.

    > [!CAUTION]
    > È consentita una sola attività figlio nel corpo dell'attività personalizzata. L'attività in questione può tuttavia essere un oggetto CompositeActivity, quale <xref:System.Activities.Statements.Sequence> o <xref:System.Activities.Statements.Flowchart>.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare un'attività](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)