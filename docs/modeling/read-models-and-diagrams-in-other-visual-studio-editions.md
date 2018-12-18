---
title: Leggere modelli e diagrammi in altre edizioni di Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: cd78d2c1e04ac37361d1e35c0f65b2e1c6637aea
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leggere modelli e diagrammi in altre edizioni di Visual Studio
Quando si apre un modello in una versione di Visual Studio che non supporta la creazione di modelli, il modello viene aperto in modalità di sola lettura. In questa modalità è possibile modificare il layout dei diagrammi, ma non modificare il modello.

 Per le versioni di Visual Studio che supportano la creazione di modelli, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Accesso a un modello e ai diagrammi
 Per leggere un diagramma di dipendenze, è necessario innanzitutto utilizzare Visual Studio per aprire il progetto di modello e quindi aprire il diagramma all'interno di esso.

 Per questo motivo, se si desidera leggere un diagramma di dipendenze, è inoltre necessario avere accesso al progetto di modello in cui è stato creato. Per eseguire questa operazione, è possibile accedere al progetto da [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] oppure ottenere una copia dei file di progetto.

> [!NOTE]
>  Non si applica alle mappe codice e ai diagrammi classi .NET generati dal codice. Questi diagrammi possono essere visualizzati indipendentemente dal progetto di modellazione.

 Per leggere un diagramma di dipendenze, il set minimo di file che è necessario è il seguente:

-   I due file per il diagramma che si desidera leggere, ad esempio, diagramma **MyDiagram.classdiagram e MyDiagram.classdiagram.layout**.

    > [!NOTE]
    >  Per i diagrammi di dipendenza, è necessario anche il file denominato * MyDiagram ***. MyDiagram**.

-   File di progetto di modellazione (**MyModel. modelproj**)

-   Il file del modello principale (**ModelDefinition\MyModel.uml**)

-   I file del pacchetto per qualsiasi pacchetto a cui fa riferimento nel diagramma (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Modifiche eseguibili in modalità di sola lettura
 Se si apre un modello e i relativi diagrammi in una versione di Visual Studio che non supporta la creazione di modelli, non sarà possibile modificare il modello. Non è possibile modificare gli elementi e le relazioni visualizzate nei diagrammi o in Esplora modelli. Tuttavia, è possibile apportare alcune modifiche al layout dei diagrammi:

-   Ridisporre le forme e i connettori nel diagramma.

-   Espandere e comprimere le forme.

 Queste modifiche possono essere salvate. Se si desidera rendere visibili ad altri utenti le modifiche, è necessario inviare almeno aggiornato **layout** file.

##  <a name="RelatedTopics"></a> Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)|Un diagramma livello mostra la struttura di un'architettura esistente o proposta. Dopo la scrittura del codice, è possibile convalidarlo automaticamente in base a un diagramma livello.|

## <a name="see-also"></a>Vedere anche

- [Creare modelli per l'app](../modeling/create-models-for-your-app.md)