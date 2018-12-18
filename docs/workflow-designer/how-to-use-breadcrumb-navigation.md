---
title: 'Procedura: utilizzare navigazioni | Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97c88a8c47bfaa2e1ccd135baec95f19a49c4e5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-breadcrumb-navigation"></a>Procedura: utilizzare l'esplorazione tramite la barra di navigazione

Esistono tre modi principali per modificare il set di attività che vengono visualizzati nella finestra di progettazione del flusso di lavoro Windows:

1.  Facendo doppio clic per analizzare un'attività figlio.

2.  Facendo clic su un pulsante nella barra di navigazione per passare a un'attività predecessore.

3.  Espandendo o comprimendo le attività sul posto.

### <a name="using-breadcrumb-navigation"></a>Usando l'esplorazione tramite la barra di navigazione

1.  Fare doppio clic su un'attività di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] per impostare l'attività radice sull'attività selezionata tramite clic. L'attività selezionata viene quindi espansa completamente alla radice e i relativi predecessori vengono mostrati nella barra di navigazione. Questa operazione viene talvolta definita analisi o annullamento dell'analisi di un'attività.

2.  Per passare a un predecessore dell'attività radice corrente, fare clic sull'attività nella barra di navigazione.

### <a name="expanding-or-collapsing-an-activity-in-place"></a>Espansione o compressione di un'attività sul posto

1.  Fare clic sulle virgolette in un'attività per espanderla o comprimerla sul posto.

2.  Quando lo stato di espansione viene modificato facendo clic sul pulsante, il nuovo stato di espansione viene salvato in XAML.

    > [!WARNING]
    > Non tutte le attività possono essere espanse sul posto. Esistono due casi in cui un'attività non può essere espansa sul posto, ovvero quando il padre dell'attività non consente l'espansione sul posto dei relativi figli (le attività di un diagramma di flusso non possono ad esempio essere espanse sul posto) o quando non è consentita l'espansione automatica dell'ActivityDesigner sul posto. Anche se nessuno degli ActivityDesigner inclusi in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] presenta quest'ultimo comportamento, è possibile che alcune attività personalizzate lo espongano.

### <a name="expanding-all-or-collapsing-all-activities"></a>Espansione o compressione di tutte le attività

1.  Utilizzare il **Espandi tutto** e **Comprimi tutto** pulsanti nell'interfaccia utente per espandere o comprimere tutte le attività sotto la radice della barra di navigazione corrente. Si noti che Espandi tutto e Comprimi tutto sono stati globali. Ciò significa che quando si modifica l'attività radice utilizzando la struttura di spostamento, espandere tutte stato o Comprimi tutto permane fino a quando non si fa clic su **ripristinare**.

2.  Dopo aver applicati un Espandi tutto o Comprimi tutto lo stato, è possibile fare clic il **ripristinare** pulsante visualizzato per tornare alla visualizzazione dello stato applicato precedentemente a ogni attività.

    > [!WARNING]
    > Se un'attività, ad esempio <xref:System.Activities.Statements.Flowchart>, è stata scelta espansione sul posto, la funzionalità associata la **Espandi tutto** e **Comprimi tutto** pulsanti sono disabilitato nel **diagramma di flusso**  finestra di progettazione. Per ulteriori informazioni sul **diagramma di flusso** della finestra di progettazione, vedere il [diagramma di flusso](../workflow-designer/flowchart-activity-designer.md) argomento.

    > [!WARNING]
    > Espandi tutto anche ha un effetto speciale **commutatore** e **TryCatch** ActivityDesigner. Quando fa clic su **Espandi tutto**, vengono visualizzati tutti i case switch e tutti i blocchi try/catch/finally. Fare clic su **ripristinare** o **Comprimi tutto** restituisce queste finestre di progettazione al relativo stato predefinito, da cui è possibile fare clic su un case/blocco singolo per visualizzarne il contenuto.