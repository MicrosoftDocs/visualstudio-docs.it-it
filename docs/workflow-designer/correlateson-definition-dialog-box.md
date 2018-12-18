---
title: Finestra di dialogo Definizione di CorrelatesOn | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 07e028a3ac5018c8a9866a6aee061d679cff74a9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="correlateson-definition-dialog-box"></a>Finestra di dialogo Definizione di CorrelatesOn
Il **CorrelatesOn** la finestra di dialogo viene utilizzata [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] per modificare il <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> proprietà di un <xref:System.ServiceModel.Activities.Receive> attività. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)]il [ricezione](../workflow-designer/receive-activity-designer.md) argomento.  
  
 La correlazione tra le attività <xref:System.ServiceModel.Activities.Receive> specifica come operazioni del servizio diverse si connettono tra loro in un flusso di lavoro.  
  
 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **CorrelatesOn** la finestra di dialogo.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|----------------|-----------------|  
|**CorrelatesWith**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.|  
|**Query XPath**|Una coppia chiave/valore che contiene le query usate per estrarre dati di correlazione dai messaggi in ingresso. Questa proprietà corrisponde alla proprietà <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Le query XPath sono incluse in un oggetto <xref:System.ServiceModel.MessageQuerySet>.|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>Per aprire la finestra di dialogo CorrelatesOn.  
 Il **ricezione** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie ovunque posizionate le attività vengono in genere. In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive. Selezionare il **ricezione** ActivityDesigner e fare clic sul pulsante con i puntini di sospensione accanto al testo (raccolta) per il **CorrelatesOn** proprietà nella griglia delle proprietà per il **definizione di CorrelatesOn**  finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ServiceModel.Activities.Receive>   
 [Aggiungere la finestra di dialogo CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [Aggiungere la finestra di dialogo di correlazione](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)