---
title: Utilizzando la finestra di progettazione del flusso di lavoro Legacy | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 700434451d8390b9875a290b428c2173953cbb8f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-legacy-workflow-designer"></a>Utilizzo di Progettazione flussi di lavoro legacy
La [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy fornita da [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] può essere usata per fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o a [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 È possibile accedervi selezionando il **.NET Framework 3.0** opzione o **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra. L'opzione predefinita [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] è **.NET Framework 4** che consente di creare [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] le applicazioni che utilizzano il [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].

 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] consente di creare graficamente le applicazioni di [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] usando dell'interfaccia utente comune di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]sono composte da passaggi del processo del flusso di lavoro chiamati attività. Per creare un flusso di lavoro, creare le attività nell'area di progettazione trascinando i rispettivi ActivityDesigner dalla **della casella degli strumenti** nell'area di progettazione.

 Nella tabella seguente sono elencate le funzionalità principali di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per Windows Workflow Foundation.

|Funzionalità|Descrizione|
|-------------|-----------------|
|Attività di trascinamento e rilascio|Trascinare le attività dal **della casella degli strumenti** nell'area di progettazione per creare un flusso di lavoro.|
|Visualizzatore proprietà|Lo standard **proprietà** finestra [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene utilizzato per configurare le proprietà di un'attività.|
|Zoom|Sul binocolo **livello di Zoom** icona si trova sotto la barra di scorrimento verticale sul lato destro dell'area di progettazione. Fare clic sul binocolo e selezionare una percentuale dello zoom per eseguire lo zoom dell'elemento grafico del flusso di lavoro avanti e indietro. È inoltre possibile utilizzare il **Pan** opzioni del cursore sull'icona lente di ingrandimento per eseguire lo zoom avanti e indietro.|
|Dettaglio|Il **Pan** icona, un cerchio contenente quattro frecce incrociate che puntano in quattro direzioni, si trova sotto la barra di scorrimento verticale sul lato destro dell'area di progettazione sotto l'icona zoom binocolo. Facendo clic sull'icona di panoramica, le opzioni del cursore seguenti verranno offerte da un menu a comparsa:<br /><br /> -La **Zoom avanti** lente di ingrandimento cursore consente di eseguire lo zoom avanti facendo clic nell'area di progettazione.<br />-La **Zoom indietro** lente di ingrandimento cursore consente di ingrandire indietro facendo clic nell'area di progettazione.<br />-La **strumento di navigazione** mano cursore consente "selezionare" e spostare la visualizzazione di un flusso di lavoro nell'area di progettazione.<br />-La **predefinito** cursore a freccia consente di tornare dagli altri cursori al cursore della freccia predefinito.|
|Scorrimento automatico|Se si ha un grande flusso di lavoro, è necessario posizionare un'attività oltre la visualizzazione visibile dell'area di progettazione. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di trascinare un'attività verso il bordo dell'area di progettazione nel punto più vicino a dove si desidera inserire l'attività. La visualizzazione dell'area di progettazione scorre automaticamente in quella direzione.|
|Smart tag|Le attività la cui configurazione non è completa o valida sono contrassegnate da un'icona di punto esclamativo. È possibile fare clic sull'icona e visualizzare un elenco a discesa di richieste di configurazione esistenti sull'attività. È quindi possibile utilizzare il **proprietà** finestra per configurare l'attività in modo appropriato. Quando tutte le proprietà sono valide per l'attività, l'icona di punto esclamativo scompare.|

## <a name="see-also"></a>Vedere anche

- [Sviluppo di flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65010)