---
title: 'Procedura: richiamare un''operazione di contratto di Windows Communication Foundation (Legacy) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: fdc27d34efef818dae30d1f54f5f3a67e7408d7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Procedura: richiamare un'operazione del contratto Windows Communication Foundation (legacy)
In questo argomento viene descritto come richiamare un'operazione di contratto [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Dopo avere trascinato un **SendActivity** attività dalla casella degli strumenti all'area di progettazione del flusso di lavoro, è necessario importare un contratto esistente e determinare quale operazione verrà richiamata dal **SendActivity** attività. Si seleziona il contratto e le operazioni tramite la [scegliere la finestra di dialogo operazione (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Se con il servizio si sta usando un file di configurazione, sarà inoltre necessario specificare un elemento <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifica la configurazione dell'endpoint che l'attività di trasmissione utilizzerà per connettersi al servizio del flusso di lavoro.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Per richiamare un'operazione di contratto WCF da un'attività SendActivity  
  
1.  Fare doppio clic su di **SendActivity** attività nella finestra di progettazione o fare clic sui puntini di sospensione accanto al **ServiceOperationInfo** proprietà il **proprietà** riquadro.  
  
2.  Quando il **Seleziona operazione** si apre la finestra di dialogo, fare clic su **importazione** nell'angolo superiore destro della finestra di dialogo.  
  
     Il [Cerca e seleziona una casella di dialogo tipo .NET (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) apre.  
  
3.  Cercare un assembly o un progetto contenente il contratto desiderato.  
  
4.  Selezionare il contratto e fare clic su **OK**.  
  
5.  In **operazioni disponibili**, selezionare l'operazione che si desidera richiamare e fare clic su **OK**.  
  
### <a name="to-specify-a-channel-token"></a>Per specificare un token del canale  
  
1.  Selezionare l'attività <xref:System.Workflow.Activities.SendActivity> nella finestra di progettazione.  
  
2.  Nel **proprietà** riquadro, specificare un nome per il <xref:System.Workflow.Activities.ChannelToken>. Questo nome identifica in modo univoco il token del canale.  
  
3.  Espandere il nodo del token del canale e specificare un nome per l'endpoint client che si desidera usare nel campo <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configurazione di endpoint con lo stesso nome nel file di configurazione verrà usata per configurare il canale.  
  
4.  Creare la configurazione dell'endpoint nel file di configurazione, se non esiste già. Per ulteriori informazioni sulla configurazione del client, vedere [panoramica dei Client WCF](/dotnet/framework/wcf/wcf-client-overview).  
  
## <a name="see-also"></a>Vedere anche  
 [Scegliere la finestra di dialogo operazione (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Procedura: implementare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)