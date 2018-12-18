---
title: Application Lifecycle Management (ALM) con app Unity | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: "12"
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload: unity
ms.openlocfilehash: 4e68024333084b6166305266dd061ef32bc0e14a
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Application Lifecycle Management (ALM) con app Unity
Lo sviluppo di app per piattaforme moderne comporta molte più attività rispetto alla semplice scrittura di codice. Queste attività definite DevOps (Development + Operations) si estendono per il ciclo di vita completo di un'app e includono pianificazione e tracciatura del lavoro, progettazione e implementazione di codice, gestione di un repository di codice sorgente, esecuzione di compilazioni, gestione di integrazioni e distribuzioni continue, test (tra cui unit test e test dell'interfaccia utente), esecuzione di varie forme di diagnostica in ambienti di sviluppo e produzione e monitoraggio delle prestazioni delle app e comportamenti dell'utente in tempo reale tramite telemetria e analisi dei dati.  

 Visual Studio insieme a Visual Studio Team Services e Team Foundation Server offrono un'ampia gamma di funzionalità DevOps, definita anche Application Lifecycle Management o ALM. Molte di queste sono applicabili a progetti multipiattaforma, inclusi i giochi e le applicazioni grafiche creati con Unity, soprattutto quando si usa C# come linguaggio di script. Tuttavia, poiché Unity ha un ambiente di sviluppo e un motore di runtime propri, diverse funzionalità di ALM non sono applicabili come avviene per altri tipi di progetti compilati in Visual Studio.  

 La tabella seguente identifica le funzionalità ALM di Visual Studio che sono o meno applicabili quando si lavora con Unity. Per informazioni dettagliate sulle funzionalità fare riferimento alla documentazione collegata.  

## <a name="agile-tools"></a>Strumenti Agile:  
 Collegamento di riferimento: **[Lavoro](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (usando Visual Studio Team Services o TFS, incluso Team Explorer Everywhere)  

 Commento generale: tutte le funzionalità di pianificazione e traccia sono indipendenti dal tipo di progetto e dai linguaggi di codifica.  

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|  
|-------------|--------------------------|-------------------------|  
|Gestione di backlog e sprint|Yes||  
|Verifica del lavoro|Yes||  
|Collaborazione nella chat team|Yes||  
|Bacheche Kanban|Yes||  
|Segnalare e visualizzare lo stato di avanzamento|Yes||  

## <a name="modeling"></a>Modellazione  
 Collegamento di riferimento: **[Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)**  

 Commento generale: anche se le funzionalità di progettazione sono indipendenti dal linguaggio di codifica o funzionano con i linguaggi .NET come C#, operano in base a un paradigma di applicazione tradizionale con gerarchie di oggetti e relazioni tra classi. La progettazione di un gioco in Unity prevede un paradigma completamente diverso, ossia relazioni di oggetti grafici, suoni, shader, script e così via. Per questo motivo, gli strumenti diagramma di modellazione di Visual Studio non sono particolarmente rilevanti per un intero progetto Unity. Possono eventualmente essere usati per gestire le relazioni negli script C#, che però costituiscono solo una parte dell'intero progetto.  

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|  
|-------------|--------------------------|-------------------------|  
|Diagrammi sequenza|No||  
|Grafici delle dipendenze|No||  
|Gerarchia di chiamata|No||  
|Progettazione classi|No||  
|Esplora architettura|No||  
|Diagrammi UML (caso di utilizzo, attività, classe, componente, sequenza e DSL)|No||  
|Diagrammi livello|No||  
|Convalida dei livelli|No||  

## <a name="code"></a>Codice  

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|  
|-------------|--------------------------|-------------------------|  
|[Usare il controllo della versione di Team Foundation](http://msdn.microsoft.com/Library/1d629052-c65d-4c5d-81eb-eaa4413fe285) o di Visual Studio Team Services|Yes|I progetti Unity sono semplicemente una raccolta di file che possono essere inseriti nei sistemi di controllo della versione come qualsiasi altro progetto, ma con alcune considerazioni speciali descritte dopo la presente tabella.|  
|[Introduzione a Git in Team Services](http://msdn.microsoft.com/Library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Yes|Vedere le note dopo la tabella.|  
|[Migliorare la qualità del codice](/visualstudio/test/improve-code-quality)|Yes||  
|[Trovare le modifiche apportate al codice e altri elementi della cronologia](../ide/find-code-changes-and-other-history-with-codelens.md)|Yes||  
|[Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)|Yes||  

 Considerazioni speciali per il controllo della versione con Unity:  

1.  Unity tiene traccia dei metadati relativi alle risorse del gioco in una singola libreria opaca, nascosta per impostazione predefinita. Per mantenere sincronizzati i file e i metadati, è necessario per rendere visibili i metadati e archiviarli in blocchi più gestibili. Per informazioni dettagliate, vedere [Using External Version Control Systems with Unity](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Uso di sistemi di controllo della versione esterni con Unity) nella documentazione di Unity.  

2.  Non tutti i file e tutte le cartelle in un progetto Unity sono appropriati per il controllo del codice sorgente, come descritto anche nel collegamento precedente. È necessario aggiungere le cartelle Assets e ProjectSettings, mentre Library e Temp non devono essere aggiunte. Per un elenco aggiuntivo dei file generati che non vengono sottoposti al controllo del codice sorgente, vedere la discussione [How to use Git for Unity3D source control?](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) (Come usare Git per il controllo del codice sorgente di Unity3D) in StackOverflow. Molti sviluppatori hanno anche discusso di questo argomento in modo indipendente.  

3.  Le risorse binarie in un progetto Unity, ad esempio trame e file audio, possono richiedere una grande quantità di spazio di archiviazione. Diversi sistemi di controllo del codice sorgente, come Git, memorizzano una copia univoca di un file per ogni modifica apportata, anche se la modifica interessa solo una piccola parte del file. Ciò può causare un aumento eccessivo dell'archivio Git. Per risolvere questo problema, gli sviluppatori Unity scelgono spesso di aggiungere al repository solo le risorse finali e usare un modo diverso per mantenere una cronologia di lavoro delle risorse, ad esempio OneDrive, DropBox o git-annex. Questo approccio funziona perché tali attività in genere non richiedono il controllo della versione insieme alle modifiche del codice sorgente. In genere, gli sviluppatori impostano anche la modalità di serializzazione delle risorse dell'editor di progetto sull'opzione per forzare il testo per archiviare i file delle scene in formato testo anziché binario, in modo da consentire operazioni di unione nel controllo del codice sorgente. Per informazioni dettagliate, vedere [Editor Settings](http://docs.unity3d.com/Manual/class-EditorManager.html) (Impostazioni dell'editor) nella documentazione di Unity.  

## <a name="build"></a>Compilazione  
 Collegamento di riferimento: **[Build and Release](/vsts/build-release/index)** (Compilazione e versione)  

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|  
|-------------|--------------------------|-------------------------|  
|Server TFS locale|Possibile|I progetti Unity vengono compilati tramite l'ambiente Unity e non tramite il sistema di compilazione di Visual Studio (se si usa Visual Studio Tools per Unity, vengono compilati gli script, ma non viene prodotto un eseguibile). Poiché è possibile [compilare progetti Unity dalla riga di comando](http://docs.unity3d.com/Manual/CommandLineArguments.html) (documentazione di Unity), si può configurare un processo MSBuild in un server TFS per eseguire i comandi Unity appropriati, a condizione che Unity sia installato nello stesso computer.<br /><br /> Unity offre anche [Unity Cloud Build](https://build.cloud.unity3d.com/landing/) che monitora un repository Git o SVN ed esegue compilazioni periodiche. Attualmente non funziona con il controllo della versione di Team Foundation o Visual Studio Team Services.|  
|Server di compilazione locale collegato a Visual Studio Team Services|Possibile|Date le stesse condizioni precedenti, è anche possibile indirizzare le compilazioni attivate tramite Visual Studio Team Services in modo che usino un computer TFS locale.  Vedere [Build and release agents](/vsts/build-release/concepts/agents/agents) (Agenti di compilazione e versione) per le istruzioni.|  
|Servizio controller ospitato di Visual Studio Team Services|No|Le compilazioni Unity non sono attualmente supportate.|  
|Definizioni di compilazione con pre e post script|Yes|Per gli script pre- e post-compilazione è anche possibile configurare una definizione di compilazione personalizzata che usa la riga di comando di Unity per eseguire una compilazione.|  
|Integrazione continuata incluse le archiviazioni gestite|Yes|Archiviazioni gestite per TFVC solo quando Git elabora un modello di richiesta di pull anziché le archiviazioni.|  

## <a name="testing"></a>Test

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|  
|-------------|--------------------------|-------------------------|  
|Pianificazione dei test, creazione di test case e organizzazione di gruppi di test|Yes||  
|Test manuali|Yes||  
|Test Manager (registrazione e riproduzione di test)|Solo dispositivi Windows ed emulatori Android||  
|Code coverage|N/D|Non applicabile perché l'esecuzione di unit test avviene in Unity e non in Visual Studio. Vedere di seguito.|  
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|In Unity, ma non Visual Studio.|Unity offre un proprio framework di unit test come parte di [Unity Test Tools](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity Asset Store). I risultati degli unit test vengono segnalati in Unity e non saranno rilevati in Visual Studio.|  
|[Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)|No|I test codificati dell'interfaccia utente si basano su controlli leggibili nell'interfaccia utente dell'app. Le app Unity sono di natura grafica e il contenuto non può quindi essere letto dagli strumenti di test codificato dell'interfaccia utente.|  

## <a name="improve-code-quality"></a>Migliorare la qualità del codice

Collegamento di riferimento: **[Migliorare la qualità del codice](/visualstudio/test/improve-code-quality)**  

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|  
|-------------|--------------------------|-------------------------|  
|[Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Yes|È possibile analizzare il codice di script C# in Visual Studio.|  
|[Ricerca del codice duplicato mediante il rilevamento del clone di codice](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Yes|È possibile analizzare il codice di script C# in Visual Studio.|  
|[Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Yes|È possibile analizzare il codice di script C# in Visual Studio.|  
|[Esplora prestazioni](../profiling/performance-explorer.md)|No|Usare il [profiler di Unity](http://docs.unity3d.com/Manual/Profiler.html) (sito Web di Unity).|  
|[Analizzare i problemi relativi alla memoria .NET Framework](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|No|Gli Strumenti di Visual Studio non includono per il framework Mono, usato da Unity, per la profilatura. Usare il [profiler di Unity](http://docs.unity3d.com/Manual/Profiler.html) (documentazione di Unity).|  

## <a name="release-management"></a>Gestione versioni  
 Collegamento di riferimento: **[Automatizzare le distribuzioni con Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|  
|-------------|--------------------------|-------------------------|  
|Gestire i processi di rilascio|Yes||  
|Distribuzione ai server per il caricamento laterale tramite script|Yes||  
|Caricare nell'app store|Partial|Sono disponibili estensioni che possono automatizzare questo processo per alcuni archivi applicazioni.  Vedere le [estensioni per Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), ad esempio l'[estensione per Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  

## <a name="monitor-with-hockeyapp"></a>Monitorare con HockeyApp  
 Collegamento di riferimento: **[Monitorare con HockeyApp](https://www.hockeyapp.net/features/)**  

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|  
|-------------|--------------------------|-------------------------|  
|Analisi degli arresti anomali, telemetria e distribuzione beta|Yes|HockeyApp risulta particolarmente utile per gestire la distribuzione beta e ottenere report sugli arresti anomali.<br /><br /> Per la telemetria di script C#, è possibile usare qualsiasi framework di analisi, a condizione che venga eseguito nella versione di .NET usata da Unity. Tuttavia, consente l'analisi solo all'interno degli script di gioco e non più in profondità nel motore di Unity. Attualmente non è disponibile un plug-in per Application Insights, ma sono disponibili plug-in per altre soluzioni di analisi, ad esempio [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) e [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). I servizi come Unity Analytics che riconoscono la natura di un progetto Unity forniscono naturalmente analisi più significative rispetto ai framework generici.|
