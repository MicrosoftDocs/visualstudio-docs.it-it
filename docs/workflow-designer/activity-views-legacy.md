---
title: "Visualizzazioni di attività (Legacy) | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 0a6658bdf0f1df76e585236497ba4ba19525b199
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="activity-views-legacy"></a>Visualizzazioni delle attività (legacy)
Per molte delle attività fornite da [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], dalle quali vengono creati i flussi di lavoro, sono disponibili numerose visualizzazioni Progettazione in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy. Quando si trascina un ActivityDesigner dal **della casella degli strumenti** nell'area di progettazione e successivamente ogni volta che si seleziona l'attività, è possibile passare tra le diverse visualizzazioni Progettazione usando il **flusso di lavoro**menu o facendovi clic sopra l'attività selezionata. Quando si sposta il puntatore sul nome di un'attività selezionata, viene inoltre visualizzato un insieme a discesa di schede che è possibile usare per passare tra le diverse visualizzazioni.  
  
 Ogni attività dispone di almeno una visualizzazione. Questa è la visualizzazione predefinita quando si trascina un ActivityDesigner dal **della casella degli strumenti** nell'area di progettazione. Questa visualizzazione predefinita dell'attività è disponibile come il **Visualizza [tipo di attività]** opzione nella scheda, ad esempio, i menu e **visualizzazione Parallel**. La maggior parte delle attività hanno visualizzazioni aggiuntive e attività diverse possono avere visualizzazioni diverse. Ad esempio, il [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) attività presenta la visualizzazione di compensazione e [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) attività dispone di un eventi vista. Molte delle attività forniti con Windows Workflow Foundation dispongono **Visualizza gestore annullamento** e **Visualizza errori** progettare viste alla visualizzazione di [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) e un [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associate.  
  
 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.  
  
|Opzione di menu/scheda|Descrizione|  
|----------------------|-----------------|  
|**Visualizzazione [tipo di attività]**|Selezionare questo menu o opzione della scheda per visualizzare la rappresentazione grafica predefinita dell'attività selezionata.|  
|**Visualizza gestore annullamento**|Selezionare questa opzione di menu o una scheda per visualizzare il [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associato all'attività selezionata.|  
|**Visualizza gestori errori**|Selezionare questa opzione di menu o una scheda per visualizzare il [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associato all'attività selezionata.|  
|**Visualizza gestore di compensazione**|Selezionare questa opzione di menu o una scheda per visualizzare il [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associate all'elemento selezionato [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Gestore di eventi di visualizzazione**|Selezionare questa opzione di menu o una scheda per visualizzare il [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) associate all'elemento selezionato di [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Per informazioni sulle visualizzazioni simili, vedere [visualizzazioni del flusso di lavoro sequenziale (Legacy)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)   
 [Visualizzazioni del flusso di lavoro sequenziale (legacy)](../workflow-designer/sequential-workflow-views-legacy.md)