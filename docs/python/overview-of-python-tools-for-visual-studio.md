---
title: Panoramica del supporto di Python in Visual Studio in Windows | Microsoft Docs
description: Riepilogo delle funzionalità di Visual Studio, il miglior ambiente IDE Python per Windows, noto anche come Python Tools for Visual Studio (PTVS)
ms.custom: ''
ms.date: 04/06/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 6b76c83db283a2cb0940d8817c04e6052157ada4
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="working-with-python-in-visual-studio-windows"></a>Utilizzo di Python in Visual Studio (Windows)

Python è un linguaggio di programmazione molto diffuso affidabile, flessibile, facile da imparare, il cui uso è gratuito in tutti i sistemi operativi e supportato sia da un'attiva community di sviluppatori che da numerose librerie gratuite. Python supporta tutte le modalità di sviluppo, tra cui applicazioni Web, servizi Web, app desktop, scripting e calcolo scientifico. Viene usato in molte università, nonché da scienziati e sviluppatori, professionisti e non professionisti. Per altre informazioni sul linguaggio, vedere [python.org](https://www.python.org) e [Python for Beginners](https://www.python.org/about/gettingstarted/) (Python per principianti).

Visual Studio è un ambiente IDE Python avanzato per Windows che offre supporto [open source](https://github.com/Microsoft/ptvs) per il linguaggio Python tramite i carichi di lavoro Sviluppo Python e Data Science (Visual Studio 2017). Visual Studio offre anche l'estensione gratuita Python Tools for Visual Studio (Visual Studio 2015 e versioni precedenti).

Python non è attualmente supportato in Visual Studio per Mac, ma è disponibile su Mac e Linux tramite Visual Studio Code (vedere le [domande e risposte](#questions-and-answers)).

Per iniziare:

- Seguire le [istruzioni di installazione](installing-python-support-in-visual-studio.md) per configurare il carico di lavoro di Python.
- Acquisire familiarità con le funzionalità Python di Visual Studio tramite le sezioni in questo articolo. È anche possibile [guardare una serie di video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) per un'introduzione a Python in Visual Studio (per un totale di 22 minuti).
- Eseguire una o più guide introduttive per creare un progetto. In caso di dubbi, iniziare con [Creare un'app Web con Flask](../ide/quickstart-python.md?context=visualstudio/python/default).
- Seguire l'esercitazione [Uso di Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) per un'esperienza completa.

## <a name="support-for-multiple-interpreters"></a>Supporto di più interpreti

La finestra **Ambienti Python** di Visual Studio (illustrata di seguito in un'ampia visualizzazione espansa) rappresenta un'unica posizione da cui gestire tutti gli ambienti Python globali, gli ambienti Conda e gli ambienti virtuali. Visual Studio rileva automaticamente le installazioni di Python in posizioni standard e consente di configurare installazioni personalizzate. Per ogni ambiente, è possibile gestire pacchetti, aprire una finestra interattiva specifica e accedere alle cartelle dell'ambiente con la massima facilità.

![Visualizzazione espansa della finestra Ambienti Python](media/environments-expanded-view.png)

Per ulteriori informazioni:

- Video (2 minuti 35 secondi): [Managing Python Environments](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) (Gestione di ambienti Python)
- Documenti: [Gestione di ambienti Python](managing-python-environments-in-visual-studio.md)
- Documenti: [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Modifica avanzata, IntelliSense e comprensione del codice

Visual Studio mette a disposizione un editor Python di prima classe, con funzionalità di colorazione della sintassi, completamento automatico in tutto il codice e in tutte le librerie, formattazione del codice, supporto per la firma, refactoring, suggerimenti relativi al tipo e rilevamento di errori con Lint (illustrato sotto). Visual Studio offre anche funzionalità esclusive, ad esempio Visualizzazione classi, Vai alla definizione, Trova tutti i riferimenti, nonché i frammenti di codice. L'integrazione diretta con la [finestra interattiva](#interactive-window) consente di sviluppare rapidamente codice Python già salvato in un file.

![Completamento di codice Python in Visual Studio](media/code-editing-completions-simple.png)

Per ulteriori informazioni:

- Video (2 minuti 30 secondi): [Editing Python code](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=r2iQH5LWE_4605918567) (Modifica di codice Python)
- Documenti: [Modifica del codice Python](editing-python-code-in-visual-studio.md)
- Documenti: [Formattazione del codice](formatting-python-code.md)
- Documenti: [Refactoring](refactoring-python-code.md)
- Documenti: [Rilevamento di errori con Lint](linting-python-code.md)
- Documenti generali sulle funzionalità di Visual Studio: [Scrittura di codice nell'Editor di testo e del codice](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Finestra interattiva

Per ogni ambiente Python noto a Visual Studio, è possibile aprire facilmente lo stesso ambiente interattivo (REPL, ciclo Read–Eval–Print) per un interprete Python direttamente all'interno di Visual Studio, anziché usare un prompt dei comandi separato. È anche possibile passare facilmente da un ambiente all'altro.

![Finestra interattiva di Python in Visual Studio](media/interactive-window.png)

Visual Studio garantisce anche una stretta integrazione tra l'editor del codice Python e la finestra interattiva. I tasti di scelta rapida **CTRL+INVIO** consentono di inviare comodamente la riga o il blocco di codice presente nell'editor alla finestra interattiva e quindi di passare alla riga successiva o al blocco successivo. Con **CTRL+INVIO** è possibile eseguire facilmente il codice un'istruzione alla volta senza dover eseguire il debugger. È anche possibile inviare codice selezionato alla finestra interattiva con la stessa combinazione di tasti e incollare facilmente codice dalla finestra interattiva nell'editor. Nel loro insieme, queste funzionalità consentono di esaminare in dettaglio un segmento di codice nella finestra interattiva e di salvare facilmente i risultati in un file nell'editor.

Visual Studio supporta anche IPython/Jupyter nel ciclo REPL, compresi tracciati inline, .NET e Windows Presentation Foundation (WPF).

Per ulteriori informazioni:

- Video (2 minuti 22 secondi: [Python Interactive Window](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567) (Finestra interattiva di Python)
- Documenti: [Finestra interattiva](python-interactive-repl-in-visual-studio.md)
- Documenti: [IPython in Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Sistema del progetto e modelli di progetto e di elemento

Visual Studio consente di gestire la complessità di un progetto man mano che le dimensioni di questo aumentano. Un progetto è molto più di una struttura di cartelle, poiché al suo interno sono presenti le informazioni sull'uso dei diversi file e sulla loro interazione reciproca. Visual Studio consente di distinguere codice dell'app, codice di test, pagine Web, JavaScript, script di compilazione e così via, abilitando le funzionalità appropriate per ogni file. Una soluzione di Visual Studio, poi, consente di gestire più progetti correlati, ad esempio un progetto Python e un progetto di estensione C++.

![Soluzione di Visual Studio contenente progetti sia Python che C++](media/projects-solution-explorer-two-projects.png)

Grazie ai modelli di progetto e di elemento, è possibile automatizzare il processo di impostazione di tipi di progetti e file diversi, risparmiando tempo prezioso ed evitando di gestire dettagli complessi e soggetti a errori. Visual Studio mette a disposizione modelli per progetti Web, Azure, data science, console e altri tipi di progetti, insieme a modelli per file quali classi, unit test, configurazioni Web di Azure, HTML e persino app Django.

[![Progetto Python e modelli di elemento in Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png)

Per ulteriori informazioni:

- Documenti: [Gestione di progetti Python](managing-python-projects-in-visual-studio.md)
- Documenti: [Modelli di progetto Python](managing-python-projects-in-visual-studio.md#project-templates)
- Documenti: [Uso di C++ e Python](working-with-c-cpp-python-in-visual-studio.md)
- Documenti generali sulle funzionalità di Visual Studio: [Modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Documenti generali sulle funzionalità di Visual Studio: [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Debug con funzionalità complete

Uno dei punti di forza di Visual Studio è un debugger avanzato. Specificamente per Python, Visual Studio include funzioni di debug in modalità mista Python/C++, debug remoto in Linux e in Azure, esecuzione del debug all'interno della finestra interattiva e unit test Python.

![Debugger di Visual Studio per Python con un'eccezione in una finestra popup](media/debugging-exception-popup.png)

Per ulteriori informazioni:

- Video: [Debugging Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=Ep5dp5LWE_3805918567) (Debug di Python), 3 minuti, 32 secondi
- Documenti: [Debug di Python](debugging-python-in-visual-studio.md)
- Documenti: [Debug in modalità mista Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Documenti: [Debug remoto in Linux](debugging-python-code-on-remote-linux-machines.md)
- Documenti: [Debug remoto in Azure](debugging-remote-python-code-on-azure.md)
- Documenti generali sulle funzionalità di Visual Studio: [Presentazione delle funzionalità del debugger di Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Strumenti di profilatura con funzionalità complete di creazione di report

La profilatura esplora come viene impiegato il tempo all'interno dell'applicazione. Visual Studio supporta la profilatura con interpreti basati su CPython e include la possibilità di confrontare le prestazioni tra esecuzioni diverse della profilatura.

[![Risultati del profiler di Visual Studio per un progetto Python](media/profiling-results.png)](media/profiling-results.png)

Per ulteriori informazioni:

- Video: [Profiling Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567) (Profilatura di Python), 3 minuti, 00 secondi
- Documenti: [Strumenti di profilatura di Python](profiling-python-code-in-visual-studio.md)
- Documenti generali sulle funzionalità di Visual Studio: [Panoramica delle funzionalità di profilatura](../profiling/profiling-feature-tour.md) (non tutte le funzionalità di profilatura di Visual Studio sono disponibili per Python).

## <a name="unit-testing-tools"></a>Strumenti per unit test

Consentono di individuare, eseguire e gestire i test in Esplora test di Visual Studio e di eseguire facilmente il debug di unit test.

![Debug di uno unit test Python in Visual Studio](media/unit-test-debugging.png)

Per ulteriori informazioni:

- Video: [Testing Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567) (Test di Python), 2 minuti, 31 secondi
- Documenti: [Strumenti di esecuzione di unit test per Python](unit-testing-python-in-visual-studio.md)
- Documenti generali sulle funzionalità di Visual Studio: [Eseguire unit test del codice](../test/unit-test-your-code.md).

## <a name="publishing-to-azure-and-azure-sdk-for-python"></a>Pubblicazione in Azure e Azure SDK per Python

Visual Studio offre supporto integrato per la pubblicazione di app Web e servizi cloud in Azure. Visual Studio include modelli di elemento `web.config` essenziali sia per il contenuto dinamico che per il contenuto statico. Il carico di lavoro Python include anche Azure SDK per Python, che semplifica l'utilizzo dei servizi di Azure da app Windows, Mac OS X e Linux.

![Pubblicare un'applicazione Python in Azure in Visual Studio](media/azure-publish-dialog.png)

Per ulteriori informazioni:

- Documenti: [Pubblicazione in Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Documenti: [Azure SDK per Python](azure-sdk-for-python.md)

## <a name="python-training-on-microsoft-virtual-academy"></a>Training su Python in Microsoft Virtual Academy

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | <ul><li>[Introduzione alla programmazione con Python](https://mva.microsoft.com/en-US/training-courses/introduction-to-programming-with-python-8360?l=lqhuMxFz_8904984382)</li><li>[Python per principianti: Stringhe e funzioni](https://mva.microsoft.com/en-US/training-courses/python-beginner-strings-and-functions-18015)</li><li>[Concetti fondamentali di Python: Elenco e cicli](https://mva.microsoft.com/en-US/training-courses/python-fundamentals-lists-and-loops-18019)</li><li>[Principali domande su Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121)</li></ul> |

## <a name="questions-and-answers"></a>Domande e risposte

**D. Il supporto di Python è disponibile in Visual Studio per Mac?**

Un  Non in questo momento, ma è possibile votare a favore della richiesta in [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac). La documentazione di [Visual Studio per Mac](/visualstudio/mac/) identifica gli attuali tipi di sviluppo che supporta. Nel frattempo, Visual Studio Code su Windows, Mac e Linux [funziona bene con Python mediante le estensioni disponibili](https://code.visualstudio.com/docs/languages/python).

**D. Cosa si può usare per compilare un'interfaccia utente con Python?**

Un  La proposta migliore in questo campo è il [progetto Qt](https://www.qt.io/qt-for-application-development/), con le associazioni per Python note come [PySide (l'associazione ufficiale)](http://wiki.qt.io/PySide) (vedere anche [PySide downloads](https://download.qt.io/official_releases/pyside/.)) e [PyQt](https://wiki.python.org/moin/PyQt). Attualmente il supporto di Python in Visual Studio non include strumenti specifici per lo sviluppo dell'interfaccia utente.

**D. Un progetto Python può produrre un file eseguibile autonomo?**

Un  Python è in genere un linguaggio interpretato, con cui il codice viene eseguito su richiesta in un ambiente in grado di supportare Python, ad esempio Visual Studio e i server Web. Visual Studio attualmente non offre la possibilità di creare un file eseguibile autonomo, ovvero un programma con un interprete Python incorporato. Tuttavia, esistono diversi metodi all'interno della community di Python per creare file eseguibili, come descritto in [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython può anche essere incorporato in un'applicazione nativa, come descritto nel post del blog, [Using CPython's Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/) (Uso del file ZIP incorporabile di CPython).

## <a name="features-matrix"></a>Matrice delle funzionalità

Le funzionalità di Python possono essere installate nelle edizioni seguenti di Visual Studio, come descritto nella [guida all'installazione](installing-python-support-in-visual-studio.md):

- [Visual Studio 2017 (tutte le edizioni)](https://www.visualstudio.com/vs/)
- [Visual Studio 2015 (tutte le edizioni)](https://www.visualstudio.com/downloads/visual-studio-2015-downloads-vs)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express per il Web, Update 2 o versione successiva
- Visual Studio 2013 Express per Desktop, Update 2 o versione successiva
- Visual Studio 2013 (Professional Edition o versione successiva)
- Visual Studio 2012 (Professional Edition o versione successiva)
- Visual Studio 2010 SP1 (Professional Edition o versione successiva; richiede .NET 4.5)

> [!Important]
> Le funzionalità vengono supportate e mantenute aggiornate in modo completo solo per la versione più recente di Visual Studio. Le funzionalità sono disponibili nelle versioni precedenti, ma non vengono mantenute aggiornate.

| Supporto per Python | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Gestione di più interpreti | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Rilevamento automatico degli interpreti più comuni | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Aggiunta di interpreti personalizzati | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Ambienti virtuali | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Installazione Pip/semplificata | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Sistema del progetto | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Nuovo progetto da codice esistente | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Mostra tutti i file | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Controllo del codice sorgente | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Integrazione con Git | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| Modifica | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Evidenziazione della sintassi | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Completamento automatico | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Supporto per la firma | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Informazioni rapide | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Visualizzatore oggetti/Visualizzazione classi | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Barra di navigazione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Vai a definizione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Passa a | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Trova tutti i riferimenti | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Rientro automatico | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Formattazione del codice | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoring - Ridenominazione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoring - Estrazione del metodo | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoring - Aggiunta/rimozione dell'importazione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Finestra interattiva | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Finestra interattiva | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IPython con grafici inline | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Desktop | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Applicazione console/Windows | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| WPF IronPython (con finestra di progettazione XAML) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Windows Form IronPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Progetto Web Django | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Progetto Web Bottle | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Progetto Web Flask | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Progetto Web generico | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Distribuzione in sito Web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Distribuzione in ruolo Web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Distribuzione in ruolo di lavoro | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Esecuzione nell'emulatore di Azure | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Debug remoto | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| Collegamento a Esplora server | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Modelli Django | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Debug | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Completamento automatico | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| Completamento automatico per CSS e JavaScript | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| Debug | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Debug | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Debug senza progetto | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Debug - Collegamento a modifica | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Debug in modalità mista | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Debug remoto (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Finestra Debug interattivo | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

<a name="matrix-profiling"></a>

| Profilatura | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Profilatura | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| Test | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Esplora test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Esegui test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Debug di test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. Il supporto Git per Visual Studio 2012 è incluso nell'estensione Visual Studio Tools for Git, disponibile in [Visual Studio Gallery](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c).

1. Per la distribuzione nel sito Web di Azure è necessario [Azure SDK per .NET 2.1 - Visual Studio 2010 SP1](http://go.microsoft.com/fwlink/?LinkId=313855). Visual Studio 2010 non è supportato nelle versioni successive.

1. Per il supporto per il ruolo di lavoro e il ruolo Web di Azure è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=323511) o versione successiva.

1. Per il supporto per il ruolo di lavoro e il ruolo Web di Azure è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o versione successiva.

1. L'editor di modelli Django in Visual Studio 2013 presenta alcuni problemi noti che vengono risolti installando l'Update 2.

1. Richiede Windows 8 o versione successiva. La finestra Collega a processo non è disponibile in Visual Studio 2013 Express per il Web, ma è comunque possibile eseguire il debug remoto del sito Web di Azure usando il comando Collega debugger (Python) in Esplora server. Il debug remoto richiede [Azure SDK per .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o versione successiva.

1. Richiede Windows 8 o versione successiva. Per il comando Collega debugger (Python) in Esplora server è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o versione successiva.

1. Richiede Windows 8 o versione successiva.

## <a name="additional-resources"></a>Risorse aggiuntive

- [WFastCGI bridge between IIS and Python](https://pypi.python.org/pypi/wfastcgi) (Ponte WFastCGI tra IIS e Python) (python.org)
- [Corsi gratuiti per Python in Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions (Domande principali su Python) alla Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)
