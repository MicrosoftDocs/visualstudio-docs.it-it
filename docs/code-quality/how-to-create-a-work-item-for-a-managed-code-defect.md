---
title: 'Procedura: Creare un elemento di lavoro per un errore del codice gestito'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 41e4a507015a630eb31c86048e785ea179899ccf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Procedura: Creare un elemento di lavoro per un errore del codice gestito

È possibile utilizzare la funzionalità di rilevamento di elementi di lavoro per registrare un elemento di lavoro all'interno di Visual Studio. Per utilizzare questa funzionalità, il progetto deve far parte del progetto Team in [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Per creare un elemento di lavoro per un errore del codice gestito

1. Nel **analisi del codice** finestra, selezionare l'avviso.

2. Scegliere **azioni**, quindi scegliere **Crea elemento di lavoro** e scegliere il tipo di elemento di lavoro da creare.

     È possibile specificare le informazioni di errore, viene creato un nuovo elemento di lavoro.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Per creare un elemento di lavoro per più difetti del codice gestito

1. Nel **elenco errori**, selezionare più avvisi e quindi fare doppio clic sugli avvisi.

2. Scegliere **Crea elemento di lavoro** e fare clic sul tipo di elemento di lavoro da creare.

     Per tutti gli avvisi selezionati è possibile specificare le informazioni sull'errore, viene creato un singolo elemento di lavoro.