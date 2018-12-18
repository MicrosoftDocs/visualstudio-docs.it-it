---
title: Application Lifecycle Management (ALM) con app Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: e2af3c9ada788c195cffb811cbfded9c43604c7a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Application Lifecycle Management (ALM) con app Xamarin
Xamarin consente di compilare le app per dispositivi mobili multipiattaforma destinate ad Android, iOS e Windows con C#, .NET e Visual Studio. Xamarin consente di condividere la maggior parte del codice tra le piattaforme e solo una piccola percentuale di codice rimane specifica della piattaforma. Per altre informazioni su Xamarin, vedere [Visual Studio e Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Lo sviluppo di app per piattaforme moderne comporta molte più attività rispetto alla semplice scrittura di codice. Queste attività definite DevOps (Development + Operations) si estendono per il ciclo di vita completo di un'app e includono pianificazione e tracciatura del lavoro, progettazione e implementazione di codice, gestione di un repository di codice sorgente, esecuzione di compilazioni, gestione di integrazioni e distribuzioni continue, test (tra cui unit test e test dell'interfaccia utente), esecuzione di varie forme di diagnostica in ambienti di sviluppo e produzione e monitoraggio delle prestazioni delle app e comportamenti dell'utente in tempo reale tramite telemetria e analisi dei dati.  
  
 Visual Studio insieme a Visual Studio Team Services e Team Foundation Server offrono un'ampia gamma di funzionalità DevOps, definita anche Application Lifecycle Management o ALM. Molti di queste sono interamente applicabili ai progetti multipiattaforma.  
  
 Ciò è particolarmente vero con le app Xamarin poiché vengono compilate con C# e .NET per i quali sono compilati alcuni strumenti ALM. Altri strumenti richiedono una stretta integrazione con gli ambienti di runtime e di compilazione. Poiché le app Xamarin vengono eseguite su piattaforme non Windows e usano l'implementazione Mono di .NET, Xamarin offre strumenti specializzati per determinate esigenze.  
  
 Le tabelle seguenti identificano le funzionalità ALM di Visual Studio di cui è possibile prevedere il corretto funzionamento con un progetto Xamarin e quelle che invece presentano limitazioni. Per informazioni dettagliate sulle funzionalità fare riferimento alla documentazione collegata.  
  
## <a name="agile-tools"></a>Strumenti Agile:  
 Collegamento di riferimento: **[Lavoro](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (usando Visual Studio Team Services o TFS, incluso Team Explorer Everywhere)  
  
 Commento generale: tutte le funzionalità di pianificazione e traccia sono indipendenti dal tipo di progetto e dai linguaggi di codifica.  
  
|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|Gestione di backlog e sprint|Yes||  
|Verifica del lavoro|Yes||  
|Collaborazione nella chat team|Yes||  
|Bacheche Kanban|Yes||  
|Segnalare e visualizzare lo stato di avanzamento|Yes||  
  
## <a name="modeling"></a>Modellazione  
 Collegamento di riferimento: **[Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)**  
  
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
|[Usare il controllo della versione di Team Foundation](http://msdn.microsoft.com/Library/1d629052-c65d-4c5d-81eb-eaa4413fe285) o di Visual Studio Team Services|Yes||  
|[Introduzione a Git in Team Services](http://msdn.microsoft.com/Library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Yes||  
|[Migliorare la qualità del codice](/visualstudio/test/improve-code-quality)|Yes||  
|[Trovare le modifiche apportate al codice e altri elementi della cronologia](../ide/find-code-changes-and-other-history-with-codelens.md)|Yes|Ad eccezione dei limiti specifici tra le piattaforme dove l'implementazione viene risolta solo dopo la fase di esecuzione.|  
|[Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)|Yes||  
  
## <a name="build"></a>Compilazione  
 Collegamento di riferimento: **[Compilazione](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|Server TFS locale|Yes|È necessario che nei computer di compilazione sia installato Xamarin e che i computer possano essere collegati a un computer OSX per la compilazione con iOS. Vedere [Configurazione di TFS per Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (sito Web Xamarin)|  
|Server di compilazione locale collegato a Visual Studio Team Services|Yes|Per istruzioni, vedere [Server di compilazione](http://msdn.microsoft.com/Library/2d258a0a-f178-4e93-9da1-eba61151af3c).|  
|Servizio controller ospitato di Visual Studio Team Services|Yes|Vedere [Build your Xamarin app](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin) (Compilare l'app Xamarin).|  
|Definizioni di compilazione con pre e post script|Yes||  
|Integrazione continuata incluse le archiviazioni gestite|Yes|Archiviazioni gestite per TFVC solo quando Git elabora un modello di richiesta di pull anziché le archiviazioni.|  
  
## <a name="testing"></a>Test

|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|Pianificazione dei test, creazione di test case e organizzazione di gruppi di test|Yes||  
|Test manuali|Yes||  
|Test Manager (registrazione e riproduzione di test)|Yes|Solo dispositivi Windows ed emulatori Android da Visual Studio. È possibile la registrazione per tutti i dispositivi con [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
|Code coverage|N/D||  
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|Yes|Per destinazioni Windows e Android, è possibile usare gli strumenti incorporati MSTest. Per eseguire unit test in Windows, Android e iOS, Xamarin consiglia NUnit. Vedere [Configurazione di TFS per Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (sito Web Xamarin).|  
|[Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)|Solo Windows|La registrazione dei test dell'interfaccia utente di Visual Studio è disponibile solo per Windows. Per tutte le piattaforme, vedere [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Migliorare la qualità del codice  
 Collegamento di riferimento: **[Migliorare la qualità del codice](/visualstudio/test/improve-code-quality)**  
  
|Funzionalità|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|[Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Yes||  
|[Ricerca del codice duplicato mediante il rilevamento del clone di codice](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Yes||  
|[Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Yes||  
|[Esplora prestazioni](../profiling/performance-explorer.md)|No|Usare invece il [Profiler Xamarin](http://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/) tramite Xamarin Studio. Si noti che il Profiler Xamarin è attualmente in versione di anteprima e non funziona ancora per le destinazioni Windows.|  
|[Analizzare i problemi relativi alla memoria .NET Framework](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|No|Gli strumenti di Visual Studio non hanno hook nel framework Mono per la profilatura.|  
  
## <a name="release-management"></a>Gestione versioni  
 Collegamento di riferimento: **[Automatizzare le distribuzioni con Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
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