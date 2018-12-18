---
title: 'Procedura: creare una libreria ActivityDesigner | Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0dc336db00f8a638cf20e6af79f2cf7ec030a5f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-activity-designer-library"></a>Procedura: creare una libreria ActivityDesigner
Gli ActivityDesigner personalizzati consentono di creare un'interfaccia utente per un'attività personalizzata o standard. È possibile controllare la complessità dell'interfaccia utente e creare più ActivityDesigner per un'attività. Questo scenario consente di creare finestre di progettazione personalizzate per diversi destinatari.

### <a name="to-create-an-activity-designer-library"></a>Per creare una libreria ActivityDesigner

1.  Avviare [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  Nel **File** dal menu **New**, quindi selezionare **progetto...**  per aprire la **nuovo progetto** la finestra di dialogo.

3.  Nel **tipi di progetto** riquadro, selezionare **flusso di lavoro** da uno di **Visual c#** o **Visual Basic** a seconda del preferito lingua.

4.  Nel **modelli** riquadro, selezionare **libreria ActivityDesigner**.

5.  Nel **nome** , immettere un nome descrittivo per il progetto per renderlo facilmente identificabile.

6.  Nel **percorso** , immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale.

7.  Nel **soluzione** casella, digitare un nome descrittivo per la soluzione, quindi fare clic su **OK**.

    > [!NOTE]
    > Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], fare clic con il pulsante destro sulla soluzione in **Esplora**e selezionare **Aggiungi**, quindi **Nuovo progetto...**  per aprire la **nuovo progetto** la finestra di dialogo. Procedere come descritto sopra in questa procedura.

8.  Il modello di progetto crea una definizione dell'ActivityDesigner in XAML mentre il file di implementazione code-behind è in codice sorgente. La finestra di progettazione del flusso di lavoro di Windows verrà visualizzato nell'area di lavoro per l'ActivityDesigner.

9. Trascinare [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)] dei controlli di **della casella degli strumenti** all'area di progettazione per usarli nell'ActivityDesigner personalizzato.  Per un esempio di come implementare un ActivityDesigner personalizzato, vedere [procedura: creare un ActivityDesigner personalizzato](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

    > [!WARNING]
    > Gli ActivityDesigner personalizzati possono essere utilizzati per le attività personalizzate nonché dell'impostazione predefinita [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]attività.

## <a name="see-also"></a>Vedere anche

- [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)