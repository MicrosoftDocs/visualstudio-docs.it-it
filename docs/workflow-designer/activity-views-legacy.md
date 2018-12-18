---
title: Visualizzazioni di attività (Legacy) | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2cc053be2f9d11a9a1f3cd48c6c9d24e366410c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="activity-views-legacy"></a>Visualizzazioni delle attività (legacy)
Molte delle attività fornite da [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], da cui i flussi di lavoro sono composte da, sono disponibili in Progettazione flussi di lavoro Windows legacy numerose visualizzazioni Progettazione. Quando si trascina un ActivityDesigner dal **della casella degli strumenti** nell'area di progettazione e successivamente ogni volta che si seleziona l'attività, è possibile passare tra le diverse visualizzazioni Progettazione usando il **flusso di lavoro**menu o facendovi clic sopra l'attività selezionata. Quando si sposta il puntatore sul nome di un'attività selezionata, viene inoltre visualizzato un insieme a discesa di schede che è possibile usare per passare tra le diverse visualizzazioni.

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

- [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)
- [Visualizzazioni del flusso di lavoro sequenziale (legacy)](../workflow-designer/sequential-workflow-views-legacy.md)