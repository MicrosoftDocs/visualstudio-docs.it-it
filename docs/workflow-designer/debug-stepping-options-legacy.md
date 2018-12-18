---
title: Eseguire il debug passo a passo opzioni (Legacy) | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61a13c4f423e0c0ff65b1dc451868695b5c5570a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="debug-stepping-options-legacy"></a>Opzioni di avanzamento nell’esecuzione del debug (legacy)
In questo argomento viene descritto come eseguire il debug [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] le applicazioni che dispongono di attività simultanee in Progettazione flussi di lavoro Windows legacy. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Quando si esegue il debug di attività legacy esecuzione simultanea, ad esempio **ParallelActivity** o **ConditionedActivityGroup**, è possibile utilizzare una delle due opzioni seguenti per esaminare il codice .

-   **Avanzamento nel ramo.** Questo metodo consente di procedere ed eseguire il debug di un particolare ramo di un'attività composta, ad esempio il **ParallelActivity** o **ConditionalActivityGroup** attività. Quando si usa quest'opzione di debug, non si noterà una modifica nel controllo dovuta all'esecuzione contemporanea di altre attività all'interno del flusso di lavoro. Il debugger avanza solo attraverso le attività del ramo attualmente selezionato mentre le altre attività del flusso di lavoro possono essere eseguite contemporaneamente. Ad esempio, per impostazione predefinita, il ramo all'estrema sinistra di un **ParallelActivity** attività e la prima attività figlio di un **ConditionedActivityGroup** attività vengono utilizzati per l'esecuzione di istruzioni. Se l’utente desidera eseguire il debug di qualsiasi altro ramo o attività figlia, un punto di interruzione esplicito deve essere posizionato su quel ramo o su quella attività figlia. Quando il punto di interruzione viene generato, l'avanzamento continua in quel ramo.

-   **Avanzamento nell'istanza.** Questa modalità di procedere consente di procedere ed eseguire il debug eseguendo contemporaneamente le attività del flusso di lavoro. Con questa opzione, si noterà che si verifica una modifica nel controllo durante l'esecuzione contemporanea di attività eseguite all'interno del flusso di lavoro.

 Per impostazione predefinita, l'opzione di avanzamento nel ramo è selezionata e gli utenti possono passare tra le due opzioni durante l'esecuzione del debug di un flusso di lavoro legacy.

 È necessario selezionare l'opzione di avanzamento dell’istanza in caso di esecuzione di debug di flussi di lavoro di macchine a stati legacy.

## <a name="see-also"></a>Vedere anche

- [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)
- [Procedura: Modificare l'opzione di avanzamento nell'esecuzione del debug (legacy)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)