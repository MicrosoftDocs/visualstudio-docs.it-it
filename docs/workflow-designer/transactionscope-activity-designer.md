---
title: ActivityDesigner TransactionScope | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 9c9b9ab609825a68edc4e2862d64bdd7cb830202
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="transactionscope-activity-designer"></a>ActivityDesigner TransactionScope
Il **TransactionScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.TransactionScope> attività.  
  
## <a name="the-transactionscope-activity"></a>Attività TransactionScope  
 L'attività <xref:System.Activities.Statements.TransactionScope> esegue in un'unica transazione l'attività contenuta. Il commit della transazione viene eseguito quando l'attività <xref:System.Activities.Statements.TransactionScope.Body%2A> e tutti gli altri partecipanti della transazione sono stati completati correttamente.  
  
### <a name="using-the-transactionscope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactionScope  
 Il **TransactionScope** ActivityDesigner è reperibile nel **transazione** categoria del **della casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**  scheda [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **visualizzazione** menu o CTRL + ALT + X.)  
  
 Il **TransactionScope** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.TransactionScope> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito TransactionScope. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **TransactionScope** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.  
  
### <a name="the-transactionscope-properties"></a>Proprietà di TransactionScope  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TransactionScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Le proprietà <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Statements.TransactionScope.Body%2A> possono essere modificate nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Le altre proprietà devono invece essere modificate nella griglia delle proprietà.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TransactionScope>. Il valore predefinito è TransactionScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Consente di specificare l'attività da eseguire in un'unica transazione. Per aggiungere il <xref:System.Activities.Statements.TransactionScope.Body%2A> attività, trascinare un'attività dal **della casella degli strumenti** nel **corpo** casella il **TransactionScope** ActivityDesigner con testo di suggerimento "rilasciare l'attività di seguito".|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Consente di specificare la proprietà <xref:System.Transactions.IsolationLevel> per questa attività <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Consente di specificare l'intervallo di tempo (nel formato 00:00:00, che indica ore:minuti:secondi) disponibile per il completamento della transazione. Il valore predefinito è 1 minuto (00:01:00).|  
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|True|Specifica il valore che indica se il flusso di lavoro deve essere interrotto se la transazione si interrompe.|  
  
## <a name="see-also"></a>Vedere anche  
 [Transazione](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensare](../workflow-designer/compensate-activity-designer.md)   
 [Conferma](../workflow-designer/confirm-activity-designer.md)