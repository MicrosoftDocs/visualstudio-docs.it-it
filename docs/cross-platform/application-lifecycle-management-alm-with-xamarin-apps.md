---
title: Application Lifecycle Management (ALM) con app Xamarin | Microsoft Docs
ms.date: 08/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 0cce9882add1443c2d9187d65b26a25081aac75b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634941"
---
# <a name="devops-with-xamarin-apps"></a>DevOps con app Xamarin

Xamarin consente di compilare le app per dispositivi mobili multipiattaforma destinate ad Android, iOS e Windows con C#, .NET e Visual Studio. Xamarin consente di condividere la maggior parte del codice tra le piattaforme e solo una piccola percentuale di codice rimane specifica della piattaforma. Per altre informazioni su Xamarin, vedere [Visual Studio e Xamarin](../cross-platform/visual-studio-and-xamarin.md).

Lo sviluppo di app per piattaforme moderne comporta molte più attività rispetto alla semplice scrittura di codice. Queste attività definite DevOps (Development + Operations) si estendono per il ciclo di vita completo di un'app e includono pianificazione e rilevamento del lavoro, progettazione e implementazione di codice, gestione di un repository di codice sorgente, esecuzione di compilazioni, gestione di integrazioni e distribuzioni continue, test (tra cui unit test e test dell'interfaccia utente), esecuzione di varie forme di diagnostica in ambienti di sviluppo e produzione e monitoraggio delle prestazioni delle app e comportamenti dell'utente in tempo reale tramite telemetria e analisi.

Visual Studio insieme a Visual Studio Team Services e Team Foundation Server offre un'ampia gamma di funzionalità DevOps. Molti di queste sono interamente applicabili ai progetti multipiattaforma. Ciò è particolarmente vero con le app Xamarin poiché vengono compilate con C# e .NET per i quali sono compilati alcuni strumenti DevOps. Altri strumenti richiedono una stretta integrazione con gli ambienti di runtime e di compilazione. Poiché le app Xamarin vengono eseguite su piattaforme non Windows e usano l'implementazione Mono di .NET, Xamarin offre strumenti specializzati per determinate esigenze.

Le tabelle seguenti identificano le funzionalità DevOps di Visual Studio di cui è possibile prevedere il corretto funzionamento con un progetto Xamarin e quelle che invece presentano limitazioni. Per informazioni dettagliate sulle funzionalità fare riferimento alla documentazione collegata.

## <a name="agile-tools"></a>Strumenti Agile:

Collegamento di riferimento: **[About Agile tools and Agile project management](/vsts/work/backlogs/overview?view=vsts)** (Informazioni sugli strumenti e la gestione di progetti Agile)

Commento generale: tutte le funzionalità di pianificazione e traccia sono indipendenti dal tipo di progetto e dai linguaggi di codifica.

|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|
|-------------|----------------------------|-------------------------|
|Gestione di backlog e sprint|Yes||
|Verifica del lavoro|Yes||
|Collaborazione nella chat team|Yes||
|Bacheche Kanban|Yes||
|Segnalare e visualizzare lo stato di avanzamento|Yes||

## <a name="modeling"></a>Modellazione

Collegamento di riferimento: **[Analizzare e modellare l'architettura](../modeling/analyze-and-model-your-architecture.md)**

Le funzionalità di progettazione sono indipendenti dal linguaggio di codifica o funzionano con i linguaggi .NET come C#. Per informazioni sugli aspetti correlati al codice, vedere [Ruoli dei diagrammi dell'architettura e della modellazione nello sviluppo del software](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools).

|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|
|-------------|----------------------------|-------------------------|
|Diagrammi sequenza|Yes||
|Grafici delle dipendenze|Yes||
|Gerarchia di chiamata|Yes||
|Progettazione classi|Yes||
|Esplora architettura|Yes||
|Diagrammi UML (caso di utilizzo, attività, classe, componente, sequenza e DSL)|Yes||
|Diagrammi livello|Yes||
|Convalida dei livelli|Yes||

## <a name="code"></a>Codice

|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|
|-------------|----------------------------|-------------------------|
|[Usare il controllo della versione di Team Foundation](/vsts/tfvc/overview?view=vsts) o di Visual Studio Team Services|Yes||
|[Introduzione a Git in Team Services](/vsts/git/gitquickstart?view=vsts&tabs=visual-studio)|Yes||
|[Migliorare la qualità del codice](../test/improve-code-quality.md)|Yes||
|[Trovare le modifiche apportate al codice e altri elementi della cronologia](../ide/find-code-changes-and-other-history-with-codelens.md)|Yes|Ad eccezione dei limiti specifici tra le piattaforme dove l'implementazione viene risolta solo dopo la fase di esecuzione.|
|[Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)|Yes||

## <a name="build"></a>Compilazione

Collegamento di riferimento: **[Build and Release](/vsts/pipelines/index?view=vsts)** (Compilazione e versione)

|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|
|-------------|----------------------------|-------------------------|
|Server TFS locale|Yes|È necessario che nei computer di compilazione sia installato Xamarin e che i computer possano essere collegati a un computer OSX per la compilazione con iOS. Vedere [Use TFVC](/vsts/tfvc/overview?view=vsts) (Usare il controllo della versione di Team Foundation)|
|Server di compilazione locale collegato a Visual Studio Team Services|Yes|Vedere [Build and release agents](/vsts/pipelines/agents/agents?view=vsts) (Agenti di compilazione e versione) per le istruzioni.|
|Servizio controller ospitato di Visual Studio Team Services|Yes|Vedere [Build your Xamarin app](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts) (Compilare l'app Xamarin).|
|Definizioni di compilazione con pre e post script|Yes||
|Integrazione continuata incluse le archiviazioni gestite|Yes|Archiviazioni gestite per TFVC solo quando Git elabora un modello di richiesta di pull anziché le archiviazioni.|

## <a name="test"></a>Test

|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|
|-------------|----------------------------|-------------------------|
|Pianificazione dei test, creazione di test case e organizzazione di gruppi di test|Yes||
|Test manuali|Yes||
|Test Manager (registrazione e riproduzione di test)|Yes|Solo dispositivi Windows ed emulatori Android da Visual Studio. È possibile la registrazione per tutti i dispositivi con [Xamarin Test Recorder](/appcenter/test-cloud/uitest/).|
|Code coverage|N/D||
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|Yes|Per destinazioni Windows e Android, è possibile usare gli strumenti incorporati MSTest. Per eseguire unit test in Windows, Android e iOS, Xamarin consiglia NUnit. Vedere [Use TFVC](/vsts/tfvc/overview?view=vsts) (Usare il controllo della versione di Team Foundation).|
|[Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)|Solo Windows|La registrazione dei test dell'interfaccia utente di Visual Studio è disponibile solo per Windows. Per tutte le piattaforme, vedere [Xamarin.UITest](/appcenter/test-cloud/uitest/).|

## <a name="improve-code-quality"></a>Migliorare la qualità del codice

Collegamento di riferimento: **[Migliorare la qualità del codice](../test/improve-code-quality.md)**

|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|
|-------------|----------------------------|-------------------------|
|[Analizzare la qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Yes||
|[Ricerca del codice duplicato mediante il rilevamento del clone di codice](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Yes||
|[Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Yes||
|[Esplora prestazioni](../profiling/performance-explorer.md)|No|Usare invece il [Profiler Xamarin](/xamarin/cross-platform/deploy-test/) tramite Xamarin Studio. Si noti che il Profiler Xamarin è attualmente in versione di anteprima e non funziona ancora per le destinazioni Windows.|
|[Analizzare i problemi relativi alla memoria .NET Framework](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|No|Gli strumenti di Visual Studio non hanno hook nel framework Mono per la profilatura.|

## <a name="release-management"></a>Gestione versioni

Collegamento di riferimento: **[Build and Release in VSTS and TFS](/vsts/pipelines/overview?view=vsts)** (Compilazione e rilascio in VSTS e TFS)

|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|
|-------------|----------------------------|-------------------------|
|Gestire i processi di rilascio|Yes||
|Distribuzione ai server per il caricamento laterale tramite script|Yes||
|Caricare nell'app store|Partial|Sono disponibili estensioni che possono automatizzare questo processo per alcuni archivi applicazioni.  Vedere le [estensioni per Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), ad esempio l'[estensione per Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitorare con HockeyApp

Collegamento di riferimento: **[Monitorare con HockeyApp](https://www.hockeyapp.net/features/)**

|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|
|-------------|----------------------------|-------------------------|
|Analisi degli arresti anomali, telemetria e distribuzione beta|Yes||