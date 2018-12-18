---
title: Ritardo ActivityDesigner | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 24ca658650c3b0eeb28261753b06082214cdb838
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="delay-activity-designer"></a>ActivityDesigner Delay
Il **ritardo** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Delay> attività.  
  
## <a name="the-delay-activity"></a>Attività Delay  
 L'attività <xref:System.Activities.Statements.Delay> ritarda l'esecuzione di un flusso di lavoro per una quantità di tempo specificata.  
  
### <a name="using-the-delay-activity-designer"></a>Utilizzo dell'ActivityDesigner Delay  
 Il **ritardo** ActivityDesigner è reperibile nel **primitive** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti**scheda della finestra il [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)  
  
 Il **ritardo** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.Delay> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito Delay. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **ritardo** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.  
  
### <a name="the-delay-properties"></a>Proprietà di Delay  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Delay> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Delay>. Il valore predefinito è Delay. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Durata del ritardo del flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà. Per specificare tale durata, digitare un valore <xref:System.TimeSpan> letterale nel formato 00:00:00 o un'espressione Visual Basic.|  
  
## <a name="see-also"></a>Vedere anche  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [Assegnare](../workflow-designer/assign-activity-designer.md)   
 [ActivityDesigner Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)