---
title: "Miglioramento della qualità del codice con i criteri di controllo del progetto Team | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c82bc929fa7633719c06569cb3dded5df651a349
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Miglioramento della qualità del codice con i criteri di archiviazione del progetto team

Quando si usa il controllo della versione di Team Foundation (TFVC), è possibile creare criteri di archiviazione per i progetti team. per applicare procedure che consentono di ottimizzare il codice e lo sviluppo dei gruppi. I criteri di archiviazione sono regole che vengono impostate a livello di progetto team e applicate nei computer degli sviluppatori prima che sia consentita l'archiviazione del codice.

È possibile specificare i seguenti criteri di archiviazione del progetto team:

- **Compilazioni**: richiede che le interruzioni di compilazione create durante una compilazione vengano corrette prima di una nuova archiviazione.

- **Commenti per gli insiemi di modifiche**: richiede che gli utenti forniscano commenti quando archiviano le modifiche.

- **Analisi codice**: richiede che venga eseguita l'analisi del codice prima dell'archiviazione.

- **Elementi di lavoro**: richiede l'associazione di uno o più elementi di lavoro all'archiviazione.

> [!IMPORTANT]
> Per usare i criteri di archiviazione, è necessario essere connessi a [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)].

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto di supporto|
|----------|------------------------|
|**Creare e usare criteri di archiviazione dell'analisi codice:** è possibile effettuare una selezione all'interno di un set standard di regole di analisi del codice oppure creare un set personalizzato.|[Creazione e uso di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>Attività correlate

|Attività|Contenuto di supporto|
|----------|------------------------|
|**Usare Analisi codice nel processo di sviluppo:** i membri del team eseguono l'analisi del codice nei propri computer di sviluppo. In Visual Studio gli sviluppatori configurano ed eseguono esecuzioni dell'analisi del codice per i singoli progetti di codice, visualizzano e analizzano i problemi rilevati dalle esecuzioni e creano elementi di lavoro per gli avvisi.|[Analisi della qualità delle applicazioni](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Creare ed eseguire unit test:** Unit test offrono a sviluppatori e tester un modo rapido per individuare errori logici nei metodi delle classi in progetti c#, Visual Basic e C++. Uno unit test può essere creato una volta ed eseguito ogni volta che il codice sorgente viene modificato per assicurarsi che non siano stati introdotti bug.|[Eseguire unit test del codice](../test/unit-test-your-code.md)|
|**Tenere traccia di elementi di lavoro e difetti:** è possibile usare elementi di lavoro per tenere traccia e gestire il lavoro e le informazioni sul progetto team. Un elemento di lavoro è un record di database che viene usato da [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] per monitorare l'assegnazione e lo stato del lavoro. Si possono usare diversi tipi di elementi di lavoro per tenere traccia di vari tipi di lavoro, ad esempio requisiti del cliente, bug del prodotto e attività di sviluppo.|[Elementi di lavoro (VSTS)](/vsts/work/work-items/index)|

## <a name="external-resources"></a>Risorse esterne

[Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside](http://go.microsoft.com/fwlink/?LinkID=255188) (Test per la distribuzione continua con Visual Studio 2012 - Capitolo 2: Testing unità: Test interni)