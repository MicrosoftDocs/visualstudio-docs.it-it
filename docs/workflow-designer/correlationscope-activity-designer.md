---
title: ActivityDesigner CorrelationScope | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 71f2ce7f69351c0e829f43f9e491304db39e6cea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="correlationscope-activity-designer"></a>ActivityDesigner CorrelationScope
Il **CorrelationScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.CorrelationScope> attività che fornisce la gestione implicita di attività di messaggistica figlio mediante un <xref:System.ServiceModel.Activities.CorrelationHandle> oggetto.  
  
## <a name="the-correlationscope-activity"></a>Attività CancellationScope  
 La proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> contenute in <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sono configurate per usare la proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> dell'attività <xref:System.ServiceModel.Activities.CorrelationScope> contenitore per eseguire la correlazione.  
  
### <a name="using-the-correlationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CorrelationScope  
 Il **CorrelationScope** ActivityDesigner è reperibile nel **messaggistica** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti** scheda sul lato sinistro del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)  
  
 Il **CorrelationScope** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area. Crea un <xref:System.ServiceModel.Activities.CorrelationScope> attività con valore predefinito è **DisplayName** correlationscope. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **CorrelationScope** ActivityDesigner o nel **DisplayName** casella del **proprietà** finestra.  
  
 Per specificare il <xref:System.ServiceModel.Activities.CorrelationHandle> utilizzato dalle attività di messaggistica figlio, fare clic su pulsante con i puntini di sospensione accanto il **CorrelatesWith** campo **proprietà** finestra per visualizzare il **Editor espressioni**  la finestra di dialogo. È possibile impostare questa proprietà anche nell'area di progettazione dell'attività.  
  
 L'attività il cui ambito all'interno della correlazione vengono specificate rilasciando le finestre di progettazione all'interno di **corpo** casella all'interno di **CorrelationScope** progettazione.  
  
### <a name="the-correlationscope-properties"></a>Proprietà di CancellationScope  
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.CorrelationScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Queste proprietà possono essere modificati in **proprietà** finestra oppure [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] progettazione superficie di attacco e spesso in entrambe.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Consente di specificare l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> usato per gestire le attività di messaggistica figlio. Se non si imposta questa proprietà, <xref:System.ServiceModel.Activities.CorrelationScope> crea automaticamente un oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> implicito.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Consente di specificare le attività all'interno dell'ambito della correlazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Ricezione](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Invia](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)