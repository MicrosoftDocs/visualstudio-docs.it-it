---
title: Panoramica del supporto di Python in Visual Studio (Windows) | Microsoft Docs
description: "Riepilogo delle funzionalità disponibili per Python in Visual Studio (noto anche come Python Tools for Visual Studio, PTVS), incluse domande e risposte e una matrice di supporto delle funzionalità nelle varie versioni di Visual Studio."
ms.custom: 
ms.date: 02/15/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: hero-article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 8693e876d56a30b31cd873861c37dbef486e7284
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="working-with-python-in-visual-studio-windows"></a>Utilizzo di Python in Visual Studio (Windows)

Python è un linguaggio di programmazione molto diffuso affidabile, flessibile, facile da imparare, il cui uso è gratuito in tutti i sistemi operativi e supportato sia da un'attiva community di sviluppatori che da numerose librerie gratuite. Python supporta tutte le modalità di sviluppo, tra cui applicazioni Web, servizi Web, app desktop, script e calcolo scientifico. Viene usato in molte università, nonché da scienziati, sviluppatori professionisti e non professionisti. Per altre informazioni sul linguaggio, vedere [python.org](https://www.python.org) e [Python for Beginners](https://www.python.org/about/gettingstarted/) (Python per principianti).

Visual Studio in Windows offre supporto [open source](https://github.com/Microsoft/ptvs) per il linguaggio Python attraverso lo sviluppo di Python e i carichi di lavoro Data Science (Visual Studio 2017), altre all'estensione gratuita Python Tools for Visual Studio (Visual Studio 2015 e versioni precedenti). Python non è attualmente supportato in Visual Studio per Mac, ma è disponibile su Mac e Linux tramite Visual Studio Code (vedere le [domande e risposte](#questions-and-answers)).

Per iniziare:

- Seguire le [istruzioni di installazione](installing-python-support-in-visual-studio.md) per configurare il carico di lavoro di Python.
- Eseguire una o più guide introduttive per creare un progetto. In caso di dubbi, iniziare con [Creare un progetto da un modello](quickstart-02-python-in-visual-studio-project-from-template.md).
- Seguire l'esercitazione [Uso di Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) per un'esperienza completa.
- Usare quindi i collegamenti nella tabella seguente per esplorare le funzionalità correlate a Python e le funzionalità di Visual Studio.

| Funzionalità | Descrizione | Documentazione generale su Visual Studio |
| --- | --- | --- |
| [Sistema del progetto di Visual Studio](managing-python-projects-in-visual-studio.md) | Rileva in modo implicito una struttura di cartelle del codice Python consentendo anche un controllo esplicito per distinguere chiaramente i vari elementi di codice dell'app, codice di test, pagine Web, JavaScript, script di compilazione e così via. | [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Modelli di progetto](managing-python-projects-in-visual-studio.md#project-templates) | Consente di creare rapidamente la struttura del progetto per console, Web, Azure, analisi scientifica dei dati e altri tipi di progetti. | [Modelli di Visual Studio](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| Supporto per più interpreti | Supporta diverse versioni di CPython e IronPython. | N/D |
| Supporto di IPython | Include il supporto per IPython/Jupyter in REPL per grafici inline, .NET e Windows Presentation Foundation (WPF). | N/D |
| [Modifica avanzata, IntelliSense e comprensione del codice](editing-python-code-in-visual-studio.md) | Colorazione della sintassi, completamento automatico in tutto il codice e in tutte le librerie, [formattazione del codice](formatting-python-code.md), supporto per la firma, visualizzazione delle classi, accesso alle definizioni, opzione per trovare tutti i riferimenti, frammenti di codice, [refactoring](refactoring-python-code.md), [PyLint](linting-python-code.md) e altro ancora. | [Writing Code in the Code and Text Editor](../ide/writing-code-in-the-code-and-text-editor.md) (Scrittura di codice nell'Editor di testo e del codice) |
| [Finestra interattiva](python-interactive-repl-in-visual-studio.md) | Fornisce un'esperienza rapida di REPL per Python e consente di evidenziare facilmente una parte del codice e di inviarla alla finestra interattiva. | N/D |
| [Debug con funzionalità complete](debugging-python-in-visual-studio.md) | Il debug può essere eseguito con o senza un progetto di Visual Studio. Include la funzionalità per eseguire il debug di un eseguibile esistente, il [debug Python/C++ in modalità mista](debugging-mixed-mode-c-cpp-python-in-visual-studio.md), il [debug remoto in Linux](debugging-python-code-on-remote-linux-machines.md) per Windows/Linux/Mac, il [debug remoto in Azure](debugging-remote-python-code-on-azure.md) e il debug all'interno della finestra interattiva. | [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md) |
| [Strumenti di profilatura con funzionalità complete di creazione report](profiling-python-code-in-visual-studio.md) | Esamina l'uso del tempo nell'applicazione e consente di confrontare le prestazioni tra diverse esecuzioni della profilatura. | [Strumenti di profilatura](../profiling/profiling-tools.md) (non tutte le funzionalità di profilatura di Visual Studio sono disponibili per Python) |
| [Strumenti per unit test](unit-testing-python-in-visual-studio.md) | Consentono di individuare, eseguire e gestire i test in Esplora test di Visual Studio e di eseguire facilmente il debug di unit test. | [Eseguire unit test del codice](../test/unit-test-your-code.md) |

Il carico di lavoro Python include anche [Azure SDK per Python](azure-sdk-for-python.md), che semplifica l'uso dei servizi Azure da applicazioni Windows, Mac OS X e Linux.

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | [Guardare una serie di video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) per un'introduzione a Python in Visual Studio (per un totale di 22 minuti). |
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | Vedere anche i video seguenti in Microsoft Virtual Academy:<ul><li>[Introduzione alla programmazione con Python](https://mva.microsoft.com/en-US/training-courses/introduction-to-programming-with-python-8360?l=lqhuMxFz_8904984382)</li><li>[Python per principianti: Stringhe e funzioni](https://mva.microsoft.com/en-US/training-courses/python-beginner-strings-and-functions-18015)</li><li>[Concetti fondamentali di Python: Elenco e cicli](https://mva.microsoft.com/en-US/training-courses/python-fundamentals-lists-and-loops-18019)</li><li>[Principali domande su Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121)</li></ul> |

## <a name="questions-and-answers"></a>Domande e risposte

**D. Il supporto di Python è disponibile in Visual Studio per Mac?**

Un  Non in questo momento, sebbene sia richiesto in [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac). La documentazione di [Visual Studio per Mac](/visualstudio/mac/) identifica gli attuali tipi di sviluppo che supporta. Nel frattempo, Visual Studio Code su Windows, Mac e Linux [funziona bene con Python mediante le estensioni disponibili](https://code.visualstudio.com/docs/languages/python).

**D. Cosa si può usare per compilare un'interfaccia utente con Python?**

Un  La proposta migliore in questo campo è il [progetto Qt](https://www.qt.io/qt-for-application-development/), con le associazioni per Python note come [PySide (l'associazione ufficiale)](http://wiki.qt.io/PySide) (vedere anche [PySide downloads](https://download.qt.io/official_releases/pyside/.)) e [PyQt](https://wiki.python.org/moin/PyQt). Attualmente il supporto di Python in Visual Studio non include strumenti specifici per lo sviluppo dell'interfaccia utente.

**D. Un progetto Python può produrre un file eseguibile autonomo?**

Un  Python è in genere un linguaggio interpretato, con cui il codice viene eseguito su richiesta in un ambiente in grado di supportare Python, ad esempio Visual Studio e i server Web. Visual Studio attualmente non offre la possibilità di creare un file eseguibile autonomo, ovvero un programma con un interprete Python incorporato. Tuttavia, esistono diversi metodi all'interno della community di Python per creare file eseguibili, come descritto in [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython può anche essere incorporato in un'applicazione nativa, come descritto nel post del blog, [Using CPython's Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/) (Uso del file ZIP incorporabile di CPython).

## <a name="features-matrix"></a>Matrice delle funzionalità

Le funzionalità di Python possono essere installate nelle edizioni seguenti di Visual Studio, come descritto nella [guida all'installazione](installing-python-support-in-visual-studio.md):

- [Visual Studio 2017 (tutte le edizioni)](https://www.visualstudio.com/vs/)
- [Visual Studio 2015 (tutte le edizioni)] (https://www.visualstudio.com/it-it/downloads/visual-studio-2015-downloads-vs)
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
