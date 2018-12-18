---
title: ActivityDesigner PickBranch | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: d583c662de31b990982b78d876bc0046e89089d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="pickbranch-activity-designer"></a>ActivityDesigner PickBranch
<xref:System.Activities.Statements.PickBranch> offre un percorso di esecuzione basato sugli eventi all'interno di un'attività <xref:System.Activities.Statements.Pick> che può essere attivata da un evento in entrata.  
  
## <a name="pickbranch"></a>PickBranch  
 Gli oggetti <xref:System.Activities.Statements.PickBranch> sono contenuti nella raccolta <xref:System.Activities.Statements.Pick.Branches%2A> di un'attività <xref:System.Activities.Statements.Pick>. Ogni oggetto <xref:System.Activities.Statements.PickBranch> è contenuto in un ramo dell'attività <xref:System.Activities.Statements.Pick> e può essere eseguito in seguito a un evento in entrata che funge da trigger. In questo modo [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] consente la modellazione di un flusso di controllo basato sugli eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick  
 Il **PickBranch** reperibili nella finestra di progettazione il **flusso di controllo** categoria del **della casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti** scheda [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X).  
  
 Due vuoto <xref:System.Activities.Statements.PickBranch> oggetti con i nomi visualizzati dei **Branch1** e **Branch2** vengono creati per impostazione predefinita come elementi di un <xref:System.Activities.Statements.Pick> attività quando il **Pick** ActivityDesigner viene inizialmente rilasciato il [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. I rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> i valori delle proprietà possono essere modificati nella **PickBranch** intestazione della finestra di progettazione o all'interno di **proprietà** finestra per ogni ramo.  
  
 Esistono due modi per aggiungere <xref:System.Activities.Statements.PickBranch> oggetti alla raccolta di un <xref:System.Activities.Statements.Pick> oggetto: trascinando e rilasciando il **PickBranch** dalla finestra di progettazione di **della casella degli strumenti** o utilizzando il menu di scelta rapida da all'interno di **Pick** area di progettazione:  
  
1.  Il **PickBranch** consente di creare un <xref:System.Activities.Statements.PickBranch> quando viene trascinato dal **della casella degli strumenti** e rilasciato in uno dei rami di un **Pick** ActivityDesigner sul [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area. I nuovi oggetti <xref:System.Activities.Statements.PickBranch> possono essere posizionati all'interno della finestra di progettazione <xref:System.Activities.Statements.Pick>, a destra o a sinistra di qualsiasi elemento <xref:System.Activities.Statements.PickBranch> esistente già contenuto nella raccolta. Quando si trascina un **PickBranch** nella finestra di progettazione il **Pick** della finestra di progettazione con il mouse, il **selezionare** finestra di progettazione utilizza una verticale di colore blu-grigio per indicare dove il <xref:System.Activities.Statements.PickBranch> viene aggiunto per una determinata posizione del mouse.  
  
2.  Fare clic destro **Pick** ActivityDesigner (ma non all'interno **PickBranch** progettazione) per visualizzare un menu di scelta rapida e scegliere **Crea ramo** per aggiungere un nuovo <xref:System.Activities.Statements.PickBranch>. Si noti che il nuovo <xref:System.Activities.Statements.PickBranch> viene aggiunto a destra dell'oggetto esistente <xref:System.Activities.Statements.PickBranch> gli oggetti il **Pick** finestra di progettazione.  
  
 Il **PickBranch** progettazione può essere espanso per visualizzare il **Trigger** e **azione** caselle o compresso facendo sui due accenti circonflessi sul lato destro delle rispettive intestazioni. Modificare il <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A> di ogni <xref:System.Activities.Statements.PickBranch> trascinando le attività nel **Trigger** e **azione** caselle delle rispettive finestre di progettazione.  
  
 Il <xref:System.Activities.Statements.PickBranch> gli oggetti nel <xref:System.Activities.Statements.Pick.Branches%2A> raccolta di un <xref:System.Activities.Statements.Pick> oggetto, possono essere riordinati trascinandoli e rilasciandoli in una nuova posizione all'interno di **selezionare** progettazione. Il **Pick** finestra di progettazione utilizza una verticale di colore blu-grigio per indicare dove il <xref:System.Activities.Statements.PickBranch> viene aggiunto per una determinata posizione del mouse.  
  
 Esistono due diverse modalità per eliminare un'attività <xref:System.Activities.Statements.PickBranch>:  
  
1.  Selezionare il **PickBranch** progettazione ed eliminarlo.  
  
2.  Selezionare il **PickBranch** rapida della finestra di progettazione, per visualizzare il menu di scelta rapida e scegliere **eliminare**.  
  
 Assicurarsi di selezionare il **PickBranch** della finestra di progettazione, selezionare una delle attività all'interno di relativo **Trigger** o **azione** caselle comporta l'eliminazione di tali attività e non il <xref:System.Activities.Statements.PickBranch> oggetto.  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>Proprietà di PickBranch in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.PickBranch> e ne viene descritto l'uso in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Il nome descrittivo visualizzato nell'intestazione del **PickBranch** finestra di progettazione. Il valore predefinito è Branch.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Ogni <xref:System.Activities.Statements.PickBranch> contiene un'azione <xref:System.Activities.Statements.PickBranch.Trigger%2A> che può richiamare l'elemento <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Ogni <xref:System.Activities.Statements.PickBranch> contiene un elemento <xref:System.Activities.Statements.PickBranch.Action%2A> che viene eseguito se attivato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)   
 [Attività Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [Uso dell'attività Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)