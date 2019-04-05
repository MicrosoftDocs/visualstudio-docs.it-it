---
title: Activity Designer TransactionScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: abed15a1ce3d406cfd5e95318dd332a677f61095
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966871"
---
# <a name="transactionscope-activity-designer"></a>ActivityDesigner TransactionScope
Il **TransactionScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.TransactionScope> attività.  
  
## <a name="the-transactionscope-activity"></a>Attività TransactionScope  
 L'attività <xref:System.Activities.Statements.TransactionScope> esegue in un'unica transazione l'attività contenuta. Il commit della transazione viene eseguito quando l'attività <xref:System.Activities.Statements.TransactionScope.Body%2A> e tutti gli altri partecipanti della transazione sono stati completati correttamente.  
  
### <a name="using-the-transactionscope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactionScope  
 Il **TransactionScope** ActivityDesigner è reperibile nel **transazione** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**  scheda della finestra [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu o CTRL + ALT + X.)  
  
 Il **TransactionScope** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.TransactionScope> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito TransactionScope. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **TransactionScope** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.  
  
### <a name="the-transactionscope-properties"></a>Proprietà di TransactionScope  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TransactionScope> e ne viene descritta la modalità di uso nella finestra di progettazione. Le proprietà <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Statements.TransactionScope.Body%2A> possono essere modificate nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Le altre proprietà devono invece essere modificate nella griglia delle proprietà.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TransactionScope>. Il valore predefinito è TransactionScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Consente di specificare l'attività da eseguire in un'unica transazione. Per aggiungere il <xref:System.Activities.Statements.TransactionScope.Body%2A> attività, rilasciare un'attività dal **della casella degli strumenti** nel **corpo** casella il **TransactionScope** ActivityDesigner con testo di suggerimento "rilasciare l'attività In questo caso".|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Consente di specificare la proprietà <xref:System.Transactions.IsolationLevel> per questa attività <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Consente di specificare l'intervallo di tempo (nel formato 00:00:00, che indica ore:minuti:secondi) disponibile per il completamento della transazione. Il valore predefinito è 1 minuto (00:01:00).|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|True|Specifica il valore che indica se il flusso di lavoro deve essere interrotto se la transazione si interrompe.|  
  
## <a name="see-also"></a>Vedere anche  
 [Transazione](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensare](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)