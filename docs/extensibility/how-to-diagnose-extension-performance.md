---
title: 'Procedura: diagnosticare le prestazioni di estensione | Documenti Microsoft'
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: "1"
author: BertanAygun
ms.author: bertaygu
manager: ghogen
ms.workload: bertaygu
ms.openlocfilehash: 1d1034cce8b2fced5af48a0a4bfa8620b56994e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="measuring-extension-impact-in-startup"></a>Misurare l'impatto di estensione nella finestra di avvio

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Concentrarsi sulle prestazioni di estensione in Visual Studio 2017

In base ai suggerimenti dei clienti, una delle aree di interesse per il rilascio di Visual Studio 2017 stato delle prestazioni di carico di avvio e di soluzione. Mentre, come il team di piattaforma Visual Studio, abbiamo lavorato per migliorare le prestazioni di caricamento di avvio e di soluzione in generale, i dati di telemetria suggerisce le estensioni installate possono anche di avere un impatto notevole in tali scenari.

Per consentire agli utenti di comprendere l'impatto, abbiamo aggiunto una nuova funzionalità in Visual Studio per notificare agli utenti di estensioni lenta. Quando Visual Studio rileva una nuova estensione che è rallentare il caricamento della soluzione o l'avvio, gli utenti vedranno una notifica nell'IDE di puntarli a una nuova finestra di dialogo "Gestire le prestazioni di Visual Studio". Questa finestra di dialogo sono accessibili anche dal menu per Sfoglia estensioni rilevate in precedenza.

![la gestione delle prestazioni di Visual Studio](media/manage-performance.png)

Questo documento è destinato agli sviluppatori di estensioni descrivendo la modalità di calcolo impatto di estensione e come si può essere analizzato in locale per verificare se un'estensione può essere visualizzata come estensione conseguenze sulle prestazioni.

## <a name="how-extensions-can-impact-startup"></a>Estensioni possano impatto di avvio

Uno dei modi più comuni per le estensioni di influire sulle prestazioni di avvio è se si sceglie di caricamento automatico in uno dei contesti dell'interfaccia utente di avvio noti, ad esempio NoSolutionExists o ShellInitialized. Questi contesti dell'interfaccia utente è essere attivati durante l'avvio e tutti i pacchetti che includono l'attributo "ProvideAutoLoad" nella relativa definizione con questi contesti verranno caricati e inizializzati in quel momento.

Quando è misurato l'impatto di un'estensione, focalizzata principalmente sul tempo impiegato da tali estensioni che sceglie di caricamento automatico nei contesti del precedenti. Misurata volte verrebbero includono ma non sono limitate a:

* Caricamento degli assembly di estensione per i pacchetti sincroni
* Tempo impiegato per il costruttore della classe del pacchetto per i pacchetti sincroni
* Tempo impiegato nel metodo di inizializzazione (o SetSite) del pacchetto per i pacchetti sincroni
* Per i pacchetti asincroni le operazioni riportate sopra, eseguire sul thread in background e pertanto vengono esclusi dal monitoraggio
* Tempo impiegato nelle operazioni asincrone pianificate durante l'inizializzazione del pacchetto per l'esecuzione sul thread principale
* Tempo impiegato per i gestori eventi, in particolare l'attivazione di shell inizializzata contesto o la modifica dello stato di zombie shell
* A partire dall'aggiornamento 3 di Visual Studio 2017, verrà inoltre avvia il monitoraggio tempo impiegato nelle chiamate di inattività prima che venga inizializzata shell. Esecuzione di operazioni lunghe nei gestori di inattività anche causare IDE non risponde e contribuiscono all'ora di avvio percepito dall'utente.

Sono state aggiunte numerose funzionalità, a partire da Visual Studio 2015, al fine di con eliminando la necessità di pacchetti di caricamento automatico, posticipare il loro carico ai casi più specifici in cui gli utenti saranno più certi di utilizzare l'estensione o ridurre un impatto di estensione durante il caricamento in modo automatico.

È possibile trovare ulteriori informazioni su queste funzionalità nei documenti seguenti:

[Contesti dell'interfaccia utente basati su regole](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): un motore basato su regole più ricco compilato in base a contesti dell'interfaccia utente consente di creare contesti personalizzati basati su tipi di progetto, caratteristiche e funzionalità. Questi contesti personalizzati possono essere utilizzati per caricare un pacchetto durante gli scenari più specifici, ad esempio la presenza di un progetto con una capacità specifica invece di avvio. o consentire [comando visibilità a un contesto personalizzato](visibilityconstraints-element.md) in base alle funzionalità di progetto o altre condizioni disponibili eliminando così la necessità di caricare un pacchetto per registrare un gestore di query dello stato di comando.

[Il supporto asincrono pacchetto](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): la nuova classe di base AsyncPackage in Visual Studio 2015 consente pacchetti di Visual Studio da caricare in background in modo asincrono se il caricamento del pacchetto è stato richiesto da un attributo di caricamento automatico o una query asincrona al servizio . Il caricamento in background consente all'IDE di fornire risposte tempestive mentre l'estensione viene inizializzato in background e non sarebbe risentirà scenari critici come carico di avvio e di soluzione.

[Servizi asincroni](how-to-provide-an-asynchronous-visual-studio-service.md): con il supporto asincrono pacchetto, è inoltre aggiunto il supporto per query sui servizi in modo asincrono ed è in grado di registrare i servizi asincroni. Stiamo lavorando soprattutto sulla conversione di servizi di Visual Studio di base per supportare query asincrona in modo che la maggior parte del lavoro in una query asincrona si verifica nel thread in background. SComponentModel (host di Visual Studio MEF) è uno dei servizi principali che ora supporta query asincrona per consentire le estensioni per supportare completamente il caricamento asincrono.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Ridurre l'impatto di auto caricare le estensioni

Se un pacchetto deve ancora essere caricato all'avvio automatico, è importante per ridurre al minimo il lavoro svolto durante l'inizializzazione del pacchetto per ridurre le probabilità di estensione che hanno un impatto di avvio.

Sono riportati alcuni esempi che potrebbe causare l'inizializzazione di pacchetto essere costosa

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Utilizzo del caricamento del pacchetto sincrono anziché caricamento asincrono del pacchetto

Perché sono stati caricati pacchetti sincrona nel thread principale per impostazione predefinita, è consigliabile proprietari di estensione che dispongono di pacchetti di caricamento automatico usare la classe di base del pacchetto asincrono come indicato in precedenza. La modifica di un pacchetto caricato automaticamente per supportare il caricamento asincrono inoltre rende più semplice risolvere i problemi riportati di seguito.

### <a name="synchronous-filenetwork-io-requests"></a>Richieste dei / o di rete nel file sincrono

Idealmente qualsiasi richiesta dei / o sincrono file o di rete deve essere evitato nel thread principale, come l'impatto dipenderà lo stato della macchina e può essere bloccato per lunghi periodi di tempo, in alcuni casi.

Tramite il caricamento asincrono del pacchetto e le API dei / o asincrone deve assicurarsi che l'inizializzazione di pacchetto non blocca il thread principale in questi casi e gli utenti possono continuare a interagire con Visual Studio, mentre le richieste dei / o eseguite in background.

### <a name="early-initialization-of-services-components"></a>Prima di inizializzazione dei servizi, componenti

Uno dei modelli comuni nell'inizializzazione del pacchetto consiste nell'inizializzare i servizi utilizzati o fornite da tale pacchetto nel metodo di costruttore o inizializzare pacchetto. Mentre in questo modo i servizi sono pronti per essere utilizzati, è anche possibile aggiungere costi non necessari per creare un pacchetto di caricamento se tali servizi non vengono utilizzati immediatamente. Tali servizi invece devono essere inizializzati su richiesta per ridurre al minimo il lavoro svolto nell'inizializzazione del pacchetto.

Per i servizi globali forniti da un pacchetto, è possibile utilizzare metodi AddService che accetta una funzione in modo differito inizializzare il servizio solo quando richiesto da un componente. Per i servizi utilizzati all'interno del pacchetto, è possibile usare Lazy<T> o AsyncLazy<T> per garantire servizi inizializzato o eseguire una query al primo utilizzo.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Misurare l'impatto di auto caricato estensioni usando il log attività

A partire da Visual Studio 2017 Update 3, log attività di Visual Studio conterrà le voci per l'impatto sulle prestazioni dei pacchetti durante il caricamento di avvio e di soluzione. Per visualizzare queste misure, è necessario avviare Visual Studio con l'opzione /log e aprire il file ActivityLog.xml.

Nel registro attività, si troverà in origine "Gestire le prestazioni di Visual Studio", le voci e avrà un aspetto simile al seguente:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Ciò significa che il pacchetto con GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" ha dedicato ms 2008 in avvio di Visual Studio. Si noti che il calcolo dell'impatto di un pacchetto come che sarà l'utente savigs vedere quando si disabilita l'estensione per il pacchetto Visual Studio vengono considerate costo di livello superiore come numero primario.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Misurare l'impatto di auto caricato estensioni utilizzando PerfView

Durante l'analisi del codice consentono di identificare i percorsi del codice che possono rallentare l'inizializzazione di pacchetto, è inoltre possibile utilizzare la traccia tramite applicazioni come PerfView per comprendere l'impatto di un carico di pacchetto di avvio di Visual Studio.

PerfView è uno strumento di traccia "wide" di sistema che consentirà di comprendere i percorsi di frequente in un'applicazione a causa dell'utilizzo della CPU o bloccare le chiamate di sistema. Di seguito è riportato un esempio rapido sull'analisi di un'estensione di esempio utilizzando PerfView disponibile all'indirizzo di [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Codice di esempio:**

Questo esempio è basato sull'esempio caso di codice riportato di seguito, che è progettato per visualizzare alcune cause comuni di ritardo:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**La registrazione di una traccia con PerfView:**

Quando si configura l'ambiente di Visual Studio con l'estensione installata, è possibile registrare una traccia di avvio aprendo PerfView e finestra di dialogo raccolta dal menu "Raccolta".

![menu raccolta perfview](media/perfview-collect-menu.png)

Le opzioni predefinite fornirà gli stack di chiamate per l'utilizzo della CPU, ma poiché si è interessati a nonché durata del blocco, è anche necessario abilitare gli stack "Tempo di Thread". Una volta pronti le impostazioni è possibile fare clic su "Start Collection" e avviare Visual Studio dopo la registrazione è stata avviata.

Prima interrompere la raccolta, è necessario assicurarsi che Visual Studio è completamente inizializzato, la finestra principale è completamente visibile e se l'estensione dispone degli elementi dell'interfaccia utente che mostrano automaticamente, sono inoltre visibili. Quando viene inizializzata l'estensione di Visual Studio è stata caricata completamente, è possibile arrestare la registrazione per analizzare la traccia.

**L'analisi di una traccia con PerfView:**

Una volta completata la registrazione PerfView verrà automaticamente aprire la traccia ed espandere le opzioni.

Ai fini di questo esempio, si intende principalmente nella vista "Thread ora stack" che è possibile trovare gruppo"Avanzate". Questa visualizzazione saranno inclusi tempo totale utilizzato in un thread da un metodo inclusi tempo CPU e tempo di blocco, ad esempio IO del disco o in attesa di handle.

 ![stack di thread ora](media/perfview-thread-time-stacks.png)

 Durante l'apertura di visualizzazione "Thread ora stack", è necessario scegliere il processo "devenv" per avviare l'analisi.

PerfView è Guida dettagliata su come leggere gli stack di tempo in un menu della Guida per l'analisi più dettagliata di thread. Ai fini di questo esempio, si desidera filtrare ulteriormente la visualizzazione, includendo solo gli stack di thread di nome e l'avvio del modulo di pacchetti.

1. Impostare "GroupPats" testo vuoto per rimuovere qualsiasi raggruppamento aggiunto per impostazione predefinita.
2. Set "IncPats" per includere una parte del nome dell'assembly e l'avvio del Thread oltre a filtro di processo esistente. In questo caso, deve essere "devenv; Thread di avvio. MakeVsSlowExtension".

A questo punto la vista verrà visualizzate solo costo associato con gli assembly correlati all'estensione. In questa vista, qualsiasi ora elencata nella colonna "SPA" (inclusivo costo) del thread di avvio è correlata per l'estensione filtrati e impatto di avvio.

Nell'esempio precedente alcuni interessano chiamata stack potrebbe essere:

1. IO che utilizzano la classe System.IO: durante inclusivo costo dei frame potrebbe non essere molto costosa nella traccia, sono causa di un problema potenziale poiché la velocità dei / o di file possono variare da computer a computer.

  ![frame dei / o di sistema](media/perfview-system-io-frames.png)

2. Bloccare le chiamate in attesa di altre operazioni asincrone: In questo caso tempo inclusivo rappresenta l'ora in cui il thread principale è bloccato al completamento del lavoro asincrono.

  ![frame di chiamata di blocco](media/perfview-blocking-call-frames.png)

Una delle altre visualizzazioni nella traccia che si riveleranno utili per determinare l'impatto sarà "Immagine carico stack". È possibile applicare gli stessi filtri come applicate alla vista "Thread ora stack" e scoprire tutti gli assembly caricati a causa il codice eseguito dal pacchetto caricato automaticamente.

È importante ridurre al minimo il numero di assembly caricati all'interno di una routine di inizializzazione del pacchetto come ogni assembly aggiuntivo comporterà i/o disco aggiuntivo che può rallentare notevolmente avvio computer lenti.

## <a name="summary"></a>Riepilogo

Avvio di Visual Studio è stata una delle aree su che è continuamente ottenere commenti e suggerimenti. L'obiettivo, come indicato in precedenza è per tutti gli utenti a un avvio coerenza indipendentemente dalla componenti ed estensioni che è stato installato e si desidera lavorare con i proprietari di estensione per contribuire a raggiungere tale obiettivo. Le indicazioni riportate sopra devono essere utile comprendere un impatto estensioni all'avvio e di evitare di dover auto carico o per caricare in modo asincrono per ridurre al minimo l'impatto sulla produttività degli utenti.
