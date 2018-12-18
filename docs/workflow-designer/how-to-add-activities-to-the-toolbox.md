---
title: "Procedura: aggiungere attività alla casella degli strumenti | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: "16"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: aff3172f5f01612923e72ad76f85205af0c31a72
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Procedura: aggiungere attività nella Casella degli strumenti
Le attività possono essere aggiunti al **della casella degli strumenti** nella soluzione in diversi modi. È possibile aggiungerli dall'interno il progetto corrente oppure fare riferimento a essi da un progetto diverso o da un assembly diverso.  
  
### <a name="to-add-an-activity-from-within-your-current-project"></a>Per aggiungere un'attività dall'interno del progetto corrente  
  
1.  Aggiungere una nuova attività personalizzata al progetto del flusso di lavoro corrente. [!INCLUDE[crabout](../test/includes/crabout_md.md)]aggiunta di una nuova attività personalizzata al progetto, vedere [procedura: aggiungere un nuovo elemento a un progetto flusso di lavoro](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).  
  
2.  Aggiungere la logica personalizzata all'attività.  
  
3.  Compilare il progetto. Se la compilazione ha esito positivo, una nuova categoria nella **della casella degli strumenti** denominato "\<*nome progetto*>" con l'attività personalizzata inclusa in tale categoria viene visualizzata.  
  
    > [!NOTE]
    >  Se la casella degli strumenti viene reimpostata, le attività personalizzate verranno rimosse, anche se la soluzione viene compilata nuovamente. Per ripopolare la casella degli strumenti con le attività personalizzate dopo che è stata reimpostata, riavviare [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
    > [!NOTE]
    >  La casella degli strumenti può mostrare solo un'attività di un nome specificato. Se due attività derivanti da assembly differenti hanno lo stesso nome della classe, solo una viene visualizzata.  
  
    > [!NOTE]
    >  Il dominio applicazione viene condiviso tra le istanze dell'editor; se vengono usate le variabili statiche, queste verranno condivise anche tra le istanze dell'editor. Se non si tratta del comportamento desiderato, un servizio deve essere usato per tenere traccia delle istanze variabili. Vedere [utilizzando il contesto di modifica ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) per informazioni sull'uso di servizi all'interno di progettazione.  
  
### <a name="to-add-an-activity-from-within-a-different-project"></a>Per aggiungere un'attività dall'interno di un altro progetto  
  
1.  Aprire una soluzione che contiene almeno un progetto flusso di lavoro e un progetto libreria attività personalizzato oppure un altro progetto flusso di lavoro che definisce un'attività personalizzata.  
  
2.  Compilare entrambi i progetti. Se la compilazione viene completata correttamente, una nuova categoria nella **della casella degli strumenti** denominato "\<*nome progetto*>" con l'attività personalizzata inclusa in tale categoria viene visualizzata.  
  
### <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Per aggiungere un'attività alla Casella degli strumenti da un assembly  
  
1.  Aprire una soluzione per flussi di lavoro.  
  
2.  Dal **strumenti** dal menu **Scegli elementi della casella degli strumenti...** .  
  
3.  Nel **Scegli elementi della casella degli strumenti** la finestra di dialogo, seleziona il **componenti System. Activities** scheda, quindi fare clic su **Sfoglia...**  per passare all'assembly che contiene l'attività personalizzata di cui si desidera aggiungere.  
  
4.  Selezionare l'assembly e fare clic su **OK**. Il componente attività personalizzata viene aggiunto all'elenco dei componenti e viene selezionato automaticamente.  
  
    1.  Fare clic su **OK** per chiudere la finestra di dialogo.  
  
5.  Per visualizzare la casella degli strumenti, selezionare **della casella degli strumenti** dal **vista** menu.  
  
6.  Viene visualizzata l'attività personalizzata nel **della casella degli strumenti** sotto la categoria che aveva lo stato attivo prima che fosse aggiunto l'elemento. Ad esempio, se il **generale** categoria è stata selezionata nella **della casella degli strumenti** prima di aggiungere l'elemento della casella degli strumenti, l'attività viene visualizzata sotto il **generale** categoria.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Progettazione flussi di lavoro](../workflow-designer/using-the-workflow-designer.md)