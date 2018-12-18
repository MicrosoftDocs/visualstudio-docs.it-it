---
title: Eseguire la transizione ActivityDesigner | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: "7"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: ba933b2eebb7193f8ee93852ce2a047f01ca4e0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="transition-activity-designer"></a>ActivityDesigner Transition
<xref:System.Activities.Statements.Transition> rappresenta la transizione tra due stati.  
  
## <a name="using-the-transition-activity-designer"></a>Uso di ActivityDesigner Transition  
 Un ActivityDesigner Transition consente di configurare una transizione tra due stati.  
  
### <a name="transition-properties-in-the-workflow-designer"></a>Proprietà di transizione in Progettazione flussi di lavoro  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.Transition> che possono essere impostate usando la finestra di progettazione flussi di lavoro e viene descritta la modalità di utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Transition>. Il valore predefinito è **T1**. Il valore può essere modificato nella griglia della proprietà, nell'intestazione della finestra di progettazione estesa di transizione e nell'intestazione della sezione di azione all'interno della finestra di progettazione espansa di transizione. <xref:System.Activities.Activity.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|  
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|Se presente, specifica un'espressione che deve restituire **True** prima che il controllo è passato allo stato di destinazione. Tale condizione può essere modificata nella griglia delle proprietà e nella finestra di progettazione espansa di transizione. Più condizioni in una transizione condivisa vengono valutate nell'ordine in cui appaiono nella finestra di progettazione di transizione. **Nota:** si noti che se il <xref:System.Activities.Statements.Transition.Condition%2A> di una transizione restituisce **False** (o tutte le condizioni di una transizione trigger condivisa restituiscono **False**), la transizione non si verificano e tutti i trigger per tutte le transizioni dallo stato verranno rinviati. In questa esercitazione, questa situazione non può verificarsi a causa della modalità con cui le condizioni vengono configurate (esistono azioni specifiche per verificare se il valore indicato è corretto o errato).|  
|**Origine**|True|Indica lo stato da cui ha origine questa transizione. Facendo clic sul nome dello stato di origine si passa dalla visualizzazione Progettazione a una visualizzazione estesa di tale stato. Questo valore viene impostato quando la transizione viene creata e non può essere modificata.|  
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|Specifica l'attività il cui completamento avvia la transizione. Per impostare questa attività, trascinare un'attività dal **della casella degli strumenti** e rilasciarla il **Trigger** sezione della transizione.|  
|<xref:System.Activities.Statements.Transition.Action%2A>|False|Specifica l'attività viene eseguita al termine dell'attività di trigger e <xref:System.Activities.Statements.Transition.Condition%2A>, se presente, restituisce **true**. Questa attività viene eseguita durante la transizione allo stato di destinazione, dopo l'esecuzione dell'attività di <xref:System.Activities.Statements.State.Exit%2A> per lo stato di origine, se presente. Quando la finestra di progettazione di transizione viene espansa, questo valore può essere impostato trascinando un'attività dal **della casella degli strumenti** e rilasciandola il **azione** sezione della transizione. Possono essere presenti più azioni per una sola transizione. Le singole azioni possono essere espanse e contratte e possono essere ordinate facendo clic sulla freccia verso l'alto o verso il basso visualizzato sull'azione quando sono presenti più azioni in una transizione.|  
|**Destinazione**|True|Indica lo stato in cui si trova la macchina a stati dopo il completamento della transizione. Ciò corrisponde alla proprietà <xref:System.Activities.Statements.Transition.To%2A> della transizione nel modello a oggetti. Facendo clic sul nome dello stato di destinazione si passa dalla visualizzazione Progettazione a una visualizzazione estesa di tale stato. Questo valore viene impostato quando viene creata la transizione e può essere modificato trascinando la freccia che connette la transizione allo stato di destinazione nella finestra di progettazione.|  
  
### <a name="creating-transitions"></a>Creazione transizioni  
 Le transizioni vengono creati trascinando una riga da uno stato a un altro, o rilasciando uno stato sui triangoli visualizzati quando lo stato viene trascinato su un altro stato. Per creare una transizione tramite l'operazione di trascinamento, posizionare il mouse sul bordo dello stato di origine e trascinare una linea dallo stato di origine allo stato di destinazione. Per creare una transizione con il rilascio, trascinare lo stato di destinazione e posizionarlo sullo stato di origine, quindi rilasciarlo su uno dei quattro triangoli visualizzati intorno allo stato di origine. Lo stato di destinazione può essere un nuovo stato trascinato dal **della casella degli strumenti**, o uno stato esistente trascinato dalla finestra di progettazione del flusso di lavoro.  
  
> [!NOTE]
>  Un singolo stato in una macchina a stati può essere composto da un massimo di 76 transizioni create mediante la finestra di progettazione flussi di lavoro. Il limite alle transizioni per uno stato per i flussi di lavoro creati all'esterno della finestra di progettazione è stabilito solo dalle risorse di sistema.  
  
 Le transizioni del trigger condivise sono il set di transizioni che condividono lo stesso evento del trigger. Un trigger condiviso consente la progressione condizionale a uno stato di destinazione in base alla valutazione delle espressioni configurate per più transizioni che condividono un evento comune del trigger. Per aggiungere altre azioni a una transizione e creare una transizione condivisa, fare clic sul cerchio che indica l'inizio della transizione desiderata e trascinarlo nello stato desiderato. La nuova transizione condividerà uno stesso trigger della transizione iniziale, ma avrà una condizione e un'azione univoche. Le transizioni condivise possono anche essere create dalla finestra di progettazione della transizione facendo **Aggiungi transizione del trigger condivisa** nella parte inferiore della finestra di progettazione di transizione e selezionando lo stato di destinazione desiderato dal  **Gli stati disponibili per la connessione** elenco a discesa.  
  
## <a name="see-also"></a>Vedere anche  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [Stato finale](../workflow-designer/finalstate-activity-designer.md)   
 [Stato](../workflow-designer/state-activity-designer.md)