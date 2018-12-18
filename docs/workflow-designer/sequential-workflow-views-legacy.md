---
title: Visualizzazioni di flusso di lavoro sequenziale (Legacy) | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6b42ba9c1c9f7dbe2beb4a741501967e4968508
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sequential-workflow-views-legacy"></a>Visualizzazioni del flusso di lavoro sequenziale (legacy)
[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] fornisce una progettazione di flussi di lavoro legacy di Windows che può essere usato per destinazione di [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] consente di creare graficamente le applicazioni di [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] usando dell'interfaccia utente comune di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]sono composte da passaggi del processo del flusso di lavoro chiamati attività. Per creare un flusso di lavoro, creare le attività nell'area di progettazione trascinando i rispettivi ActivityDesigner dalla **della casella degli strumenti** nell'area di progettazione.

 Quando si crea un flusso di lavoro sequenza, ovvero un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), sono disponibili tre visualizzazioni del flusso di lavoro. Queste visualizzazioni sono accessibili dal **flusso di lavoro** menu e dal menu di scelta rapida nell'area di progettazione.

 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.

|Opzione di menu/scheda|Descrizione|
|----------------------|-----------------|
|**Visualizzazione flusso di lavoro sequenziale**|Fare doppio clic su area di progettazione e seleziona il **Visualizza flusso di lavoro sequenziale** opzione dal menu di scelta rapida per visualizzare il **flusso di lavoro sequenziale** visualizzazione, che mostra le attività basate su grafica rappresentazione del flusso di lavoro sequenza. Oppure selezionare **Visualizza flusso di lavoro sequenziale** dal **flusso di lavoro** menu.|
|**Visualizza gestore annullamento**|Fare doppio clic su area di progettazione e seleziona il **Visualizza gestore annullamento** opzione dal menu di scelta rapida per visualizzare il **flusso di lavoro sequenziale** cui viene mostrata la [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) attività associata con il flusso di lavoro. Oppure selezionare **Visualizza gestore annullamento** dal **flusso di lavoro** menu.|
|**Visualizza gestori errori**|Fare doppio clic su area di progettazione e seleziona il **Visualizza gestori errori** opzione dal menu di scelta rapida per visualizzare il **errori** cui viene mostrata la [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) attività associata con il flusso di lavoro. Oppure selezionare **Visualizza gestori errori** dal **flusso di lavoro** menu.|

 Per ulteriori informazioni sulle visualizzazioni simili, vedere [visualizzazioni di attività (Legacy)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Vedere anche

- [Visualizzazioni delle attività (legacy)](../workflow-designer/activity-views-legacy.md)
- [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Modalità di creazione del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65014)