---
title: "Strumenti di test, scenari e funzionalità per sviluppatori | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: unit testing, create unit tests
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 0da910ddf48d0f270aa5e624628d0d6b937e9ae1
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Strumenti di test, scenari e funzionalità per sviluppatori

Gli unit test consentono di mantenere l'integrità del codice. Visual Studio offre agli sviluppatori un'ampia gamma di potenti strumenti e tecniche da usare durante il test delle applicazioni:

**Scenari e funzionalità:**

* [Evitare le regressioni e assicurare il code coverage con IntelliTest](#intellitest)
* [Test dell'interfaccia utente con interfaccia utente codificata e Selenium](#ui-testing)
* [Unit test efficaci con il code coverage di Visual Studio](#unit-testing)
* [Esecuzione di unit test con qualsiasi framework usando la funzionalità Esplora Test a prestazioni elevate](#test-explorer)
* [Introduzione agli unit test](getting-started-with-unit-testing.md)

<a name="intellitest"></a>
## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Evitare le regressioni e assicurare il code coverage con IntelliTest

Nei gruppi di unit test tradizionali ogni test case rappresenta un tipico scenario di utilizzo e le asserzioni corrispondono alla relazione tra input e output.  Verificare solo alcuni scenari può essere sufficiente, ma gli sviluppatori esperti sanno che i bug si annidano anche nel codice testato nel modo migliore, quando gli input corretti ma non testati causano risposte errate.

IntelliTest consente di ottimizzare il code coverage ed evitare le regressioni.
IntelliTest riduce significativamente l'impegno necessario per creare e gestire unit test per codice nuovo o esistente. 

![IntelliTest in azione](media/devtest-intellitest.png)

* [Introduzione a IntelliTest con Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [Post di blog su IntelliTest](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx)
* [Video su IntelliTest](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Generare unit test per il codice con IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Manuale di riferimento per IntelliTest](intellitest-manual/index.md)

<a name="ui-testing"></a>
## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Test dell'interfaccia utente con interfaccia utente codificata e Selenium

Testare l'interfaccia utente (UI) con le soluzioni più popolari o approvate dalla community.
I test codificati dell'interfaccia utente consentono di creare test completamente automatici per convalidare le funzionalità e il comportamento dell'interfaccia utente dell'applicazione.
Sono in grado di automatizzare il testing dell'interfaccia utente in diverse tecnologie, tra cui le app UWP basate su XAML, le app browser e le app di SharePoint.

Sia che si scelgano i test codificati dell'interfaccia utente più evoluti, sia che si usino test generici basati su browser con Selenium, Visual Studio offre tutti gli strumenti necessari. 

![Test dell'interfaccia utente con interfaccia utente codificata](media/devtest-codeduitest.png)

* [Usare l'automazione dell'interfaccia utente per testare il codice](use-ui-automation-to-test-your-code.md)
* [Creazione, modifica e gestione di un test codificato dell'interfaccia utente](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testare app UWP con test codificati dell'interfaccia utente](test-windows-store-8-1-apps-with-coded-ui-tests.md)
* [Testare app di Windows Phone 8.1 e UWP con test codificati dell'interfaccia utente](test-windows-phone-8-1-apps-with-coded-ui-tests.md)
* [Test delle applicazioni di SharePoint 2010 con test codificati dell'interfaccia utente](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Lab sull'esecuzione di test codificati dell'interfaccia utente con Visual Studio Enterprise](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

<a name="unit-testing"></a>
## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Unit test efficaci con il code coverage di Visual Studio

Per determinare quale percentuale del codice del progetto viene effettivamente testata dai test codificati come unit test, è possibile usare la funzionalità code coverage di Visual Studio. Per una protezione efficace dai bug, i test devono analizzare o "coprire" gran parte del codice.

L'analisi di code coverage può essere applicata sia al codice gestito (CLI) che a quello non gestito (nativo).

Il code coverage è un'opzione per l'esecuzione dei metodi di test utilizzando Esplora test. Nella tabella dei risultati viene illustrata la percentuale di codice che è stata eseguita per ogni assembly, classe e metodo. Inoltre, nell'editor standard viene visualizzato il codice testato.

![Test con Visual Studio Team Services e Team Foundation Server](media/devtest-codecoverage.png)

* [Uso di code coverage per determinare la quantità di codice testato](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Lab su unit test, code coverage e analisi dei cloni di codice con Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Personalizzazione dell'analisi code coverage](customizing-code-coverage-analysis.md)

<a name="test-explorer"></a>
## <a name="unit-testing-with-any-framework-using-the-high-performance-test-explorer"></a>Esecuzione di unit test con qualsiasi framework usando la funzionalità Esplora Test a prestazioni elevate

Esplora test consente agli sviluppatori di creare, gestire e ottenere il massimo vantaggio dall'esecuzione di unit test.

![Esplora test di Visual Studio](media/devtest-testexplorer.png)

* [Eseguire unit test del codice](unit-test-your-code.md)
* [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md)
* [Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md)
* [Installare framework di unit test di terze parti](install-third-party-unit-test-frameworks.md)

Visual Studio è anche estendibile e consente l'uso di adattatori di unit test di terze parti come NUnit e xUnit.net. Inoltre, la funzionalità di clonazione del codice implica la produzione di software di qualità elevata poiché consente di identificare i blocchi di codice semanticamente simile che possono essere candidati per le normali operazioni di refactoring o correzione di bug.

![Integrazione con test di terze parti](media/devtest-thirdparty.png)

## <a name="see-also"></a>Vedere anche

* [Introduzione agli unit test](getting-started-with-unit-testing.md)
* [Post di blog su come velocizzare l'esecuzione di unit test in Team Foundation Server](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/30/speeding-up-test-execution-in-tfs.aspx)
* [Post di blog sull'esecuzione di unit test paralleli e sensibili al contesto](https://blogs.msdn.microsoft.com/visualstudioalm/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Lab su unit test, code coverage e analisi dei cloni di codice con Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
