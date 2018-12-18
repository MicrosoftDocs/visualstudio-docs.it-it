---
title: Analizzare e modellare l'architettura
ms.date: 11/04/2016
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 704eee0122cfa5e0d70c910d4f5e55ff1732e670
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="analyze-and-model-your-architecture"></a>Analizzare e modellare l'architettura
Verificare che l'app soddisfi i requisiti di architettura utilizzando l'architettura di Visual Studio e strumenti per progettare e modellare l'applicazione di modellazione.

* Comprendere più facilmente il codice del programma esistente tramite Visual Studio per visualizzare la struttura, il comportamento e le relazioni del codice.

* Informare il team necessario per rispettare le dipendenze dell'architettura.

* Creare modelli con diversi livelli di dettaglio in tutto il ciclo di vita dell'applicazione nel contesto del processo di sviluppo.

Vedere [Scenario: modificare la progettazione mediante la visualizzazione e modellazione](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="to"></a>A

|||
|-|-|
|**Visualizzare il codice**:<br /><br /> -Consente di visualizzare il codice dell'organizzazione e le relazioni creando mappe del codice. Visualizzare le dipendenze tra assembly, spazi dei nomi, classi, metodi e così via.<br />-Consente di visualizzare la struttura di classe e i membri per un progetto specifico tramite la creazione di diagrammi classi dal codice.<br />-Trovare conflitti tra il codice e la progettazione mediante la creazione di diagrammi di dipendenza per convalidare il codice.|-   [Visualizzare il codice](../modeling/visualize-code.md)<br />-   [Utilizzo di classi e altri tipi (Progettazione classi)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: Comprensione progettazione dal codice con le mappe del codice Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Video: Convalidare le dipendenze dei propri architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Definire l'architettura**:<br /><br /> : Consente di definire e applicare vincoli sulle dipendenze tra i componenti del codice tramite la creazione di diagrammi di dipendenza.|-   [Video: Convalidare le dipendenze di architettura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Convalidare il sistema con i requisiti e la progettazione desiderata**<br /><br /> : Convalida delle dipendenze del codice con diagrammi di dipendenza che descrivono l'architettura desiderata e impedire modifiche che potrebbe essere in conflitto con la progettazione.|-   [Video: Convalidare le dipendenze di architettura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Condividere modelli, diagrammi e mappe codice usando il controllo della versione di Team Foundation**:<br /><br /> -Inserire le mappe del codice, i progetti e i diagrammi deoendency nel controllo della versione di Team Foundation in modo da poterli condividere.| |
|**Personalizzare modelli e diagrammi**:<br /><br /> -Creare linguaggi specifici di dominio.|-   [SDK di modellazione per Visual Studio - linguaggi specifici di dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generare testo usando i modelli T4**:<br /><br /> -Utilizzare blocchi di testo e la logica di controllo all'interno dei modelli per generare file basati su testo.<br /> -Compilazione di modelli T4 con MSBuild inclusi in Visual Studio|-   [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)|

Per individuare le versioni di Visual Studio che supportano le singole funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-their-uses"></a>Tipo di modelli e relativi usi

|**Tipo di modello e usi tipici**|
|-------------------------------------|
|**Mappe codice**<br /><br /> Le mappe codice consentono di visualizzare l'organizzazione e le relazioni nel codice.<br /><br /> Usi tipici:<br /><br /> -Esaminare il codice programma in modo da comprendere meglio la struttura e le relative dipendenze, come aggiornarlo e stimare il costo della proposta di modifiche.<br /><br /> Vedere:<br /><br /> -   [Mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Usare le mappe codice per il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Trovare problemi potenziali usando gli analizzatore delle mappe codice](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Diagramma di dipendenza**<br /><br /> Dipendenza diagrammi consentono di definire la struttura di un'applicazione come un set di livelli o blocchi con dipendenze esplicite. È possibile eseguire la convalida per trovare conflitti tra le dipendenze nel codice e le dipendenze descritte in un diagramma di dipendenze.<br /><br /> Usi tipici:<br /><br /> -Stabilizzare la struttura dell'applicazione apportando diverse modifiche durante il ciclo di vita.<br />-Prima di archiviare le modifiche apportate al codice, individuare i conflitti di dipendenza non intenzionali.<br /><br /> Vedere:<br /><br /> -   [Creare diagrammi dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md)<br />-   [Convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md)|
|**Linguaggio specifico di dominio (DSL)**<br /><br /> Un linguaggio DSL è una notazione progettata per uno scopo specifico. In Visual Studio, è generalmente grafico.<br /><br /> Usi tipici:<br /><br /> -Consente di generare o configurare parti dell'applicazione. Per sviluppare la notazione e gli strumenti sono necessarie alcune operazioni. Il risultato può essere più adatto al dominio rispetto alla personalizzazione di un modello UML.<br />-Per progetti di grandi dimensioni o nelle linee di prodotto in cui l'investimento nello sviluppo del linguaggio DSL e dei relativi strumenti è dato dall'uso in più di un progetto.<br /><br /> Vedere:<br /><br /> -   [SDK di modellazione per Visual Studio - linguaggi specifici di dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Dove è possibile ottenere altre informazioni?

[Visual Studio Visualization and Modeling Tools Forum](http://go.microsoft.com/fwlink/?LinkId=184720)

## <a name="see-also"></a>Vedere anche

- [Novità](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps e Application Lifecycle Management](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
