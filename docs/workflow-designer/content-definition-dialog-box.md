---
title: La finestra di dialogo Definizione contenuto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: "3"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: c87180f1f1c0b2c578977021b6a9511e629d10bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="content-definition-dialog-box"></a>Finestra di dialogo Definizione contenuto
Il **definizione contenuto** la finestra di dialogo viene utilizzata [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] per configurare il **contenuto** le proprietà del <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> attività. [!INCLUDE[crabout](../test/includes/crabout_md.md)]gli ActivityDesigner che utilizzano questa casella, vedere il [inviare](../workflow-designer/send-activity-designer.md), [ricezione](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) argomenti.  
  
 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **Inizializza correlazione** la finestra di dialogo.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|----------------|-----------------|  
|**Messaggio**|Specifica il contenuto del messaggio con il **i dati del messaggio** casella di testo espressione e il tipo utilizzando il **tipo di messaggio** casella di riepilogo a discesa. Per impostazione predefinita, il **definizione contenuto** utilizza il <xref:System.ServiceModel.Activities.ReceiveMessageContent>, che prevede un <xref:System.ServiceModel.Channels.Message> o un tipo nella definizione del servizio del flusso di lavoro di contratto di messaggio.|  
|**Parametri**|Fare clic su di **parametri** pulsante di opzione per utilizzare <xref:System.ServiceModel.Activities.ReceiveParametersContent>, che prevede un contratto dati. Usare la griglia dei dati per impostare una raccolta generica di coppie chiave/valore <xref:System.Activities.OutArgument> i cui valori vengono assegnati ai parametri variabili nel flusso di lavoro corrente.|  
  
 Il **definizione contenuto** la finestra di dialogo viene utilizzata la **inviare**, **ricezione**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** finestre di progettazione. La procedura di accesso è simile per tutte le finestre. In questo esempio verrà usata la finestra di progettazione Receive.  
  
 Il **ricezione** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie ovunque posizionate le attività vengono in genere. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare il **ricezione** ActivityDesigner e fare clic sul pulsante con i puntini di sospensione accanto al testo (contenuto) per il **contenuto** proprietà nella griglia delle proprietà per il **definizione contenuto**finestra di dialogo.  
  
 Il contenuto può essere specificato all'interno di **messaggio** sezione per un <xref:System.ServiceModel.Activities.ReceiveMessageContent> attività o all'interno di **parametro** sezione per un <xref:System.ServiceModel.Activities.ReceiveParametersContent> attività.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida dell'interfaccia utente della finestra di progettazione dei flussi di lavoro](../workflow-designer/workflow-designer-ui-help.md)