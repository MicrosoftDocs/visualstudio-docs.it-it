---
title: Aggiungere la finestra di dialogo CorrelationInitializers | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 4c4d8e07aa172aef524b4d85bda5ad8efdfb509f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="add-correlationinitializers-dialog-box"></a>Finestra di dialogo Aggiungi inizializzatori di correlazione
Il **Aggiungi inizializzatori di correlazione** la finestra di dialogo viene utilizzata [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] per configurare il **CorrelationInitializers** le proprietà del <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply> attività. [!INCLUDE[crabout](../test/includes/crabout_md.md)]gli ActivityDesigner che utilizzano questa casella, vedere il [inviare](../workflow-designer/send-activity-designer.md), [ricezione](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) argomenti.  
  
 Gli inizializzatori di correlazione della raccolta specificata con questa finestra di dialogo possono inizializzare correlazioni tra le attività di messaggistica basate su query, di contesto, di contesto di callback o correlazioni richiesta-risposta.  
  
 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **Aggiungi inizializzatori di correlazione** la finestra di dialogo.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|----------------|-----------------|  
|**Aggiungi inizializzatore**|Fare clic su di **Aggiungi initialize** casella per aggiungere un ulteriore inizializzatore alla raccolta.|  
|**Tipo di correlazione**|Consente di specificare il tipo di inizializzatore di correlazione. Sono disponibili quattro tipi:<br /><br /> 1.  Un inizializzatore di correlazione di callback che consente di specificare un oggetto <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Un inizializzatore di correlazione di contesto che consente di specificare un oggetto <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Un inizializzatore di correlazione richiesta-risposta che consente di specificare un oggetto <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Un inizializzatore di correlazione query che consente di specificare un oggetto <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Per modificare il **CorrelationType**<br /><br /> 1.  Scheda alla riga specifica nel **Aggiungi inizializzatore** DataGrid.<br />2.  Premere Ctrl + Tab per impostare lo stato attivo **CorrelationTypeComboBox**<br />3.  Premere Alt + freccia giù per aprire la **ComboBox** e modificarlo.|  
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso e in uscita. Questo elenco è valido solo in caso di utilizzo di tipi <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Per avviare la finestra di dialogo Aggiungi inizializzatori di correlazione  
 Il **Aggiungi inizializzatori di correlazione** la finestra di dialogo viene utilizzata la **inviare**, **ricezione**, **ReceiveAndSendReply**, e  **SendAndReceiveReply** finestre di progettazione. Accesso è simile in ogni caso e quello che prevede il **ricezione** finestra di progettazione viene utilizzato per illustrare la procedura.  
  
 Il **ricezione** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie ovunque posizionate le attività vengono in genere. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare il **ricezione** ActivityDesigner e fare clic sul pulsante con i puntini di sospensione accanto al testo (raccolta) per il **CorrelationInitializers** proprietà nella griglia delle proprietà per il **Aggiungi Inizializzatori di correlazione** finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere la finestra di dialogo di correlazione](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)