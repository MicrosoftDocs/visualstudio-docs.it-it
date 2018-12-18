---
title: Testing unità in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f8b2ec475a4c9d8cf5799c6f429519704329c2cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="unit-test-your-code"></a>Eseguire unit test del codice

Gli unit test rappresentano per sviluppatori e tester un modo rapido per verificare la presenza di errori di logica nei metodi delle classi in progetti C#, Visual Basic e C++.

Gli strumenti di unit test includono:

* **Esplora test**: è possibile eseguire unit test e visualizzare i risultati in **Esplora Test**. È possibile usare qualsiasi framework di unit test, incluso un framework di terze parti, purché provvisto di un adattatore per **Esplora test**.

* **Framework per unit test di Microsoft per il codice gestito**: viene installato con Visual Studio e offre un framework per testare il codice .NET.

* **Framework per unit test di Microsoft per C++**: viene installato come parte del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Offre un framework per testare codice nativo. Anche i framework Google Test, Boost.Test e CTest sono inclusi e sono disponibili adattatori di terze parti per framework di test aggiuntivi. Per altre informazioni, vedere [Scrittura di unit test per C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Strumenti di code coverage**: è possibile determinare la quantità di codice del prodotto sottoposta agli unit test da un singolo comando in Esplora test.

* **Framework di isolamento di Microsoft Fakes**: può creare classi e metodi sostitutivi per il codice di sistema e di produzione che creano le dipendenze nel codice sottoposto a test. L'implementazione di delegati falsi per una funzione consente di controllare il comportamento e l'output dell'oggetto di dipendenza.

È anche possibile creare [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) che esplorano il codice .NET per generare dati di test e un gruppo di unit test. Per ogni istruzione nel codice viene generato un input di test che eseguirà l'istruzione. Viene eseguita un'analisi del caso per ogni branch condizionale nel codice.

## <a name="key-tasks"></a>Attività chiave

Usare gli argomenti seguenti per la comprensione e la creazione di unit test:

|Attività|Argomenti correlati|
|-----------|-----------------------|
|**Guide introduttive e procedure dettagliate:** usare gli argomenti seguenti per ottenere informazioni sugli unit test in Visual Studio da esempi di codice.|-   [Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Guida introduttiva allo sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Aggiunta di unit test alle applicazioni C++ esistenti](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)|
|**Unit test con Esplora test:** informazioni su come Esplora test può agevolare la creazione di unit test più produttivi ed efficienti.|-   [Nozioni fondamentali sugli unit test](../test/unit-test-basics.md)<br />-   [Creare un progetto di unit test](../test/create-a-unit-test-project.md)<br />-   [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)<br />-   [Installare framework di unit test di terze parti](../test/install-third-party-unit-test-frameworks.md)|
|**Testing unità di codice gestito:**|-   [Scrittura di unit test per .NET Framework con il framework unit test di Microsoft per codice gestito](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**Eseguire unit test del codice**|-   [Scrittura di unit test per C-C++ con il framework di unit test Microsoft per C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Isolamento degli unit test**|-   [Isolamento del codice sottoposto a test con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Usare code coverage per identificare la percentuale del codice del progetto in fase di test:** informazioni sulla funzionalità code coverage degli strumenti di test di Visual Studio.|-   [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Eseguire analisi di stress e prestazioni usando test di carico:** è possibile creare un test di carico e aggiungervi gli unit test per isolare problemi di prestazioni e di stress nell'applicazione.|-   [Caricare i test (VSTS e TFS)](/vsts/load-test/)|
|**Impostare quality gate:** è possibile creare quality gate che stabiliscano l'esecuzione dei test prima dell'archiviazione del codice, in modo da garantire la qualità di quest'ultimo.|-   [Check-in policies (VSTS)](/vsts/tfvc/add-check-policies) (Criteri di archiviazione (VSTS))|
|**Impostare le opzioni di test:** ad esempio, è possibile specificare dove archiviare i risultati dei test.|[Configurazione di unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Documentazione di riferimento API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> descrive lo spazio dei nomi UnitTesting, che rende disponibili attributi, eccezioni, asserzioni e altre classi che supportano il testing unità.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> descrive lo spazio dei nomi UnitTesting.Web, che estende lo spazio dei nomi UnitTesting offrendo il supporto per gli unit test ASP.NET e dei servizi Web.

## <a name="see-also"></a>Vedere anche

- [Migliorare la qualità del codice](/visualstudio/test/improve-code-quality)
