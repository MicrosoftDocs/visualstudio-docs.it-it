---
title: "Procedura: implementare un'operazione di contratto di Windows Communication Foundation (Legacy) | Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71bf4e4e6f5abc1d2984362396f21f3c613de795
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Procedura: implementare un'operazione del contratto di Windows Communication Foundation (legacy)
In questo argomento viene descritto come implementare un [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] operazione mediante Progettazione flussi di lavoro Windows legacy che ha come destinazione del contratto di [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Dopo avere trascinato un **ReceiveActivity** attività dalla casella degli strumenti all'area di progettazione del flusso di lavoro, è necessario creare un nuovo [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] contratto o importare un contratto esistente e implementare le operazioni. Selezionare e/o creare il contratto e le operazioni tramite la [scegliere la finestra di dialogo operazione (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).

### <a name="to-implement-a-wcf-contract-operation"></a>Per implementare un'operazione del contratto WCF

1.  Fare doppio clic su di **ReceiveActivity** attività nella finestra di progettazione o fare clic sui puntini di sospensione accanto al **ServiceOperationInfo** proprietà il **proprietà** riquadro.

2.  Eseguire una delle operazioni seguenti:

    -   Fare clic su **Aggiungi contratto** nell'angolo superiore destro della finestra di dialogo. Vengono creati un nuovo contratto e una nuova operazione [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].

         oppure

    -   Fare clic su **importazione** nell'angolo superiore destro della finestra di dialogo. Il [Cerca e seleziona una casella di dialogo tipo .NET (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) apre. Cercare un assembly o un progetto contenente il contratto desiderato. Selezionare il contratto e fare clic su **OK**.

     Dopo aver creato o importato un contratto, sarà possibile aggiungervi nuove operazioni. Per aggiungere una nuova operazione, selezionare il contratto e fare clic su **operazione Add** nell'angolo superiore destro della finestra di dialogo. Dopo aver inserito tutte le operazioni, andare al passaggio 3.

3.  Selezionare l'operazione che si desidera associare il **ReceiveActivity** attività. È possibile modificare la definizione dell'operazione modificando il nome, i parametri, le proprietà e le impostazioni relative alle autorizzazioni.

     Per modificare il nome, immettere il nuovo nome nella **nome operazione** casella di testo.

     Fare clic su di **parametri** tab per accedere ai parametri dell'operazione. È possibile modificare il nome, il tipo o la direzione di un parametro così come aggiungere o eliminare parametri dall'operazione.

     Fare clic su di **proprietà** scheda per accedere alla funzionalità di exchange supportati e livello di messaggio di operazione protezione dell'operazione.

     Fare clic su di **autorizzazioni** tab per specificare quale gruppo è consentito per implementare l'operazione.

4.  Fare clic su **OK** e **ReceiveActivity** attività visualizzerà il nome dell'operazione per l'operazione che sta implementando.

5.  Inserire le attività del flusso di lavoro si intende utilizzare per l'implementazione di tale operazione all'interno di **ReceiveActivity** attività.

## <a name="see-also"></a>Vedere anche

- [Finestra di dialogo Seleziona operazione (legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Procedura: richiamare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)