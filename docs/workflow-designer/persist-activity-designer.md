---
title: ActivityDesigner Persist | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 3bd0ef80e5255a828ad31ebfa2398ff6f8b1a1e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="persist-activity-designer"></a>ActivityDesigner Persist
Il **Persist** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Persist> attività.  
  
## <a name="the-persist-activity"></a>Attività Persist  
 L'attività <xref:System.Activities.Statements.Persist> salva un flusso di lavoro su disco, se possibile. Non è possibile eseguire l'attività <xref:System.Activities.Statements.Persist> in un'area non permanente come, ad esempio, all'interno di un'attività <xref:System.Activities.Statements.TransactionScope>. Se si usa un'attività <xref:System.Activities.Statements.Persist> in un ambito non permanente, viene generata un'eccezione in fase di esecuzione.  
  
### <a name="using-the-persist-activity-designer"></a>Utilizzo dell'ActivityDesigner Persist  
 Il **Persist** ActivityDesigner è reperibile nel **Runtime** categoria del **della casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti** scheda (in alternativa, selezionare **della casella degli strumenti** dal **vista** menu o CTRL + ALT + X.)  
  
 Il **Persist** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Crea un <xref:System.Activities.Statements.Persist> attività con valore predefinito è **DisplayName** Persist. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **Persist** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.  
  
### <a name="the-persist-properties"></a>Proprietà di Persist  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Persist> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Persist>. Il valore predefinito è Persist. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Runtime](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)