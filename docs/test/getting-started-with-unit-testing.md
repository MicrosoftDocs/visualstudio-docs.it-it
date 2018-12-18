---
title: 'Introduzione agli unit test: creare piani di test | Microsoft Docs'
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: unit testing, create unit test plans
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: e6789c3a8ddb9b0aa317df0d2362d39946069cbd
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="get-started-with-unit-testing"></a>Introduzione agli unit test

Visual Studio consente di definire ed eseguire gli unit test per mantenere l'integrità del codice, garantire il code coverage e individuare gli errori e i problemi prima dei clienti.

<a name="create-tests"></a>
## <a name="create-unit-tests"></a>Creare unit test

Creare unit test ed eseguirli frequentemente per assicurarsi che il codice funzioni correttamente.

1. Creare un progetto di unit test.
        
   ![Aggiungere un progetto di unit test a una soluzione](media/createunittest1.png)
    
1. Assegnare un nome al progetto.
        
   ![Modello di progetto di unit test](media/createunittest2.png)
  
   Il progetto viene aggiunto alla soluzione.
    
   ![Progetto di unit test in Esplora soluzioni](media/createunittest5.png)
    
1. Nel progetto di unit test aggiungere un riferimento al progetto da testare.
        
   ![Aggiungere un riferimento al progetto di unit test](media/createunittest6.png)
    
1. Selezionare il progetto contenente il codice da testare.
        
   ![Selezionare il riferimento da aggiungere](media/createunittest7.png)
    
1. Aggiungere codice all'unit test.

   ![Aggiungere codice all'unit test](media/createunittest8.png) 

È anche possibile creare stub di metodo di unit test con il comando [**Crea unit test**](create-unit-tests-menu.md).
Oppure è possibile usare un altro [framework di unit test](#frameworks) per creare i test per linguaggi di codice differenti.

![Uso del comando Crea unit test](media/createunittestcommand2.png)

## <a name="run-unit-tests"></a>Eseguire unit test

1. Aprire Esplora test.
        
   ![Aprire Esplora Test nel menu Test](media/rununittest1.png) 

1. Eseguire gli unit test.
        
   ![Eseguire unit test in Esplora test](media/rununittest2.png) 

   In Esplora test è possibile visualizzare gli unit test superati e non superati.
      
   ![Esaminare i risultati degli unit test in Esplora test](media/rununittest3.png) 

## <a name="view-live-unit-test-results"></a>Visualizzare i risultati degli unit test in tempo reale

Se si usa il framework di test MSTest, xUnit o NUnit in Visual Studio 2017 o versione successiva, è possibile visualizzare in tempo reale i risultati degli unit test nell'interfaccia utente di Visual Studio.

1. Attivare la funzionalità Live Unit Testing dal menu **Test**.

   ![Attivare Live Unit Testing](media/live-test-results-start.png) 

1. Visualizzare i risultati dei test nella finestra dell'editor di codice durante la scrittura e la modifica del codice.

   ![Puntare e fare clic sugli indicatori dei risultati dei test](media/live-test-results-ui.png) 

1. Puntare e fare clic sugli indicatori dei risultati dei test per visualizzare altre informazioni.

   ![Visualizzare i risultati dei test](media/live-test-results-details.png) 

Per informazioni dettagliate, vedere [Live Unit Testing in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/live-unit-testing-visual-studio-2017-rc/).

<a name="intellitest"></a>
## <a name="generate-unit-tests-with-intellitest"></a>Generare unit test con IntelliTest

Quando si esegue IntelliTest, è possibile visualizzare facilmente i test non superati e aggiungere l'eventuale codice necessario per correggerli. È possibile scegliere quali dei test generati salvare in un progetto di test per fornire un gruppo di regressione. Quando si modifica il codice, eseguire nuovamente IntelliTest per mantenere i test generati sincronizzati con le modifiche apportate al codice. Per la procedura, vedere [Generare unit test per il codice con IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

![Generare unit test con IntelliTest](media/intellitest.png)

<a name="unit-tests"></a>
## <a name="run-unit-tests-with-test-explorer"></a>Eseguire unit test con Esplora test

Esplora Test consente di eseguire unit test da Visual Studio o progetti unit test di terze parti, raggruppare i test in categorie, filtrare l'elenco dei test, nonché creare, salvare ed eseguire playlist di test. È anche possibile eseguire il debug dei test e analizzare code coverage e prestazioni dei test. Per informazioni, vedere [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md).

![Esecuzione di unit test con Esplora test](media/testexplorer.png)

<a name="code-coverage"></a>
## <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Usare la funzionalità code coverage per determinare la quantità di codice testato

Per determinare quale percentuale del codice del progetto viene effettivamente testata dai test codificati come unit test, è possibile utilizzare la funzionalità code coverage di Visual Studio. Per una protezione efficace dai bug, i test devono analizzare o "coprire" gran parte del codice. Per le procedure, vedere [Usare la funzionalità code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

![Uso di code coverage per determinare la quantità di codice testato](media/codecoverage.png)

## <a name="q--a"></a>Domande e risposte

<!-- BEGINSECTION class="m-qanda" -->

<a name="frameworks"></a>
####D: È possibile eseguire unit test in Visual Studio se si usa un framework di unit test diverso?

R: Sì, usare il plug-in specifico del framework in modo che Visual Studio Test Runner possa funzionare con quel framework. Di seguito sono riportati alcuni dei [plug-in dei framework di unit test per Visual Studio](http://go.microsoft.com/fwlink/?LinkID=246630).

1. Usare Gestione estensioni di Visual Studio per scaricare il plug-in che interessa.
        
   ![Selezionare i plug-in di unit test di terze parti con Gestione estensioni](media/install3rdpartyunittestframeworks1.png) 

1. Scaricare il plug-in da Visual Studio Gallery in Strumenti/Test o cercarlo se si conosce il nome.
        
   ![Scaricare il plug-in](media/install3rdpartyunittestframeworks2.png) 

1. Creare un progetto Libreria di classi.
        
   ![Creare un progetto di libreria di classi](media/create3rdpartyunittest1.png) 

   Aggiungere il progetto alla soluzione.
    
   ![Assegnare un nome al progetto di libreria di classi e aggiungerlo](media/create3rdpartyunittest3.png) 

1. Nel progetto di libreria di classi eseguire NuGet per installare il plug-in.

   ![Gestire i pacchetti NuGet per installare il plug-in](media/create3rdpartyunittest3a.png) 

   [NuGet](https://www.nuget.org/) è un'estensione di Visual Studio che si può usare per aggiungere e aggiornare librerie e strumenti per i progetti.

1. Installare il plug-in. Se si conosce il nome, è possibile cercarlo online.

   ![Installare il framework di terze parti](media/create3rdpartyunittest4.png) 

   Nel progetto è presente un riferimento al framework.
        
   ![Il riferimento per il framework di unit test di terze parti viene aggiunto alla soluzione](media/create3rdpartyunittest6.png) 

1. Nel progetto di libreria di classi aggiungere un riferimento al progetto da testare.
        
   ![Aggiungere un riferimento al progetto](media/createunittest6.png) 

1. Selezionare il progetto contenente il codice da testare.
        
   ![Selezionare il progetto di codice da testare](media/createunittest7.png) 

1. Aggiungere codice all'unit test.

   ![Aggiungere codice all'unit test](media/create3rdpartyunittest7.png)   

<!-- ENDSECTION -->

## <a name="see-also"></a>Vedere anche

* [Comando Crea unit test](create-unit-tests-menu.md)
* [Generare unit test per il codice con IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md)
* [Uso di code coverage per determinare la quantità di codice testato](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Migliorare la qualità del codice](improve-code-quality.md)
