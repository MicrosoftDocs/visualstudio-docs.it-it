---
title: 'Procedura: aggiungere un nuovo elemento a un progetto flusso di lavoro (Legacy) | Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1699b3f2d16bb481a7efb744eed58d395dbc8773
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>Procedura: aggiungere un nuovo elemento a un progetto flusso di lavoro [legacy]
Dopo aver creato un progetto di flusso di lavoro utilizzando la finestra di progettazione del flusso di lavoro Windows legacy fornita da [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] che si riferisce al [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], è possibile aggiungere [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] gli elementi e altri noti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elementi in modo dal progetto.

 Nella tabella seguente sono elencati gli elementi [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] che è possibile aggiungere a un progetto flusso di lavoro.

|Item|Descrizione|
|----------|-----------------|
|Attività|Attività con definizione di attività in un file di codice della finestra di progettazione e codice utente in un file di codice separato.|
|Attività (con separazione del codice)|Definizione di attività espressa come markup del flusso di lavoro e codice utente in un file di codice separato.|
|Flusso di lavoro sequenziale (codice)|Flusso di lavoro sequenziale con definizione del flusso di lavoro in un file di codice della finestra di progettazione e codice utente in un file di codice separato.|
|Flusso di lavoro sequenziale (con separazione del codice)|Flusso di lavoro sequenziale con definizione del flusso di lavoro espressa come markup del flusso di lavoro e codice utente in un file di codice separato.|
|Flusso di lavoro di una macchina a stati (codice)|Flusso di lavoro di una macchina a stati con definizione del flusso di lavoro in un file di codice della finestra di progettazione e codice utente in un file di codice separato.|
|Flusso di lavoro della macchina a stati (con separazione del codice)|Flusso di lavoro della macchina a stati con definizione del flusso di lavoro espressa come markup del flusso di lavoro e codice utente in un file di codice separato.|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Per aggiungere un nuovo elemento a un progetto flusso di lavoro

1.  Nel **progetto** menu, fare clic su **aggiungere un nuovo elemento**.

     Il **aggiungere un nuovo elemento** verrà visualizzata la finestra di dialogo.

2.  Selezionare un elemento.

     La tabella precedente elenca le selezioni di Windows Workflow Foundation disponibili.

3.  Fare clic su **Aggiungi** ad aggiungere l'elemento al progetto flusso di lavoro.

## <a name="see-also"></a>Vedere anche

- [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)