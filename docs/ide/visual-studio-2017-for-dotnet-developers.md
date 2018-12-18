---
title: Visual Studio 2017 per sviluppatori .NET | Microsoft Docs
description: "Panoramica delle funzionalità di Visual Studio 2017 che consentono di scrivere codice .NET più efficiente in modo più veloce."
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: article
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: a834f9781ff51779b2216bd7de9dd3e449c9360a
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="visual-studio-2017-for-net-developers"></a>Visual Studio 2017 per sviluppatori .NET

## <a name="smart-code-editor"></a>Editor di codice intelligente

[Documentazione: Uso di IntelliSense](using-intellisense.md)  
[Documentazione: Funzionalità dell'editor intelligente](writing-code-in-the-code-and-text-editor.md)

Visual Studio è in grado di comprendere in modo approfondito il codice grazie al compilatore .NET ("Roslyn") e offre funzionalità di modifica intelligenti quali la colorazione della sintassi, il completamento del codice, il controllo ortografico delle variabili, la risoluzione dei tipi non importati, la creazione della struttura, i visualizzatori di struttura, [CodeLens](find-code-changes-and-other-history-with-codelens.md), la gerarchia delle chiamate, la visualizzazione di informazioni rapide al passaggio del mouse, la Guida sui parametri, oltre a strumenti per il refactoring, l'applicazione di azioni rapide e la generazione di codice.

![Editor di codice intelligente di Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

## <a name="navigate-and-search-your-codebase"></a>Esplorare la codebase ed eseguire ricerche al suo interno

[Documentazione: Spostamento nel codice](navigating-code.md)

È possibile spostarsi rapidamente all'interno del codice .NET passando a qualsiasi dichiarazione di file, tipo, membro o simbolo con il collegamento *Vai a tutti* (**Ctrl + T**). È anche possibile trovare tutti i riferimenti di un simbolo o di un valore letterale nel codice, inclusi i riferimenti tra linguaggi .NET diversi (**Maiusc + F12**), nonché usare i comandi di esplorazione mirati per passare direttamente alle definizioni di simboli (**F12**) o alle implementazioni di questi (**Ctrl + F12**).

![Vai a tutti e Trova tutti i riferimenti](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

## <a name="live-code-analysis-for-code-quality"></a>Analisi codice in tempo reale per la qualità del codice

[Documentazione: Refactoring e azioni rapide](refactoring-code-generation-quick-actions.md)

Visual Studio mette a disposizione funzionalità di diagnostica del codice in tempo reale per migliorare la qualità del codice grazie al rilevamento di errori e di codice potenzialmente problematico. Sono anche disponibili azioni rapide (**Ctrl+.**) per risolvere i problemi rilevati all'interno del documento, del progetto o della soluzione. Abilitare l'*analisi della soluzione completa* per individuare eventuali problemi all'interno dell'intera soluzione, anche se i relativi file non sono aperti nell'editor.

Con **Ctrl +.** è anche possibile usare i suggerimenti di codice per apprendere le procedure consigliate, effettuare lo stub, la generazione o il refactoring del codice e adottare nuove funzionalità del linguaggio .

![Applicare correzioni rapide e refactoring tramite il menu Lampadina](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

## <a name="unit-testing"></a>Testing unità

[Documentazione: Testing unità in Visual Studio](../test/improve-code-quality.md)

È possibile eseguire l'unit test, compreso il debug, con i framework di testing MSTest, NUnit o XUnit per qualsiasi applicazione destinata a .NET Framework, .NET Standard o .NET Core. È anche possibile esaminare e rivedere i test in *Esplora test* e rendersi conto immediatamente dell'impatto delle modifiche al codice sull'unit test all'interno dell'editor con *Live Unit Testing* (solo SKU Enterprise). 

![Live Unit Testing in Visual Studio](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

## <a name="code-consistency-and-style"></a>Coerenza e stile del codice

[Documentazione: Impostazioni personalizzate e portabili per l'editor](create-portable-custom-editor-options.md)  
[Documentazione: Impostazioni di EditorConfig relative allo stile del codice per .NET](editorconfig-code-style-settings-reference.md)

Visual Studio consente la configurazione di convenzioni di scrittura del codice, rilevando le violazioni di stile, e presenta correzioni rapide per risolvere i problemi di stile con i tasti di scelta rapida **Ctrl +.** . Per configurare e imporre le convenzioni di formattazione, denominazione e stile del codice in un repository, consentendo eccezioni a livello di progetto e di file, è possibile usare *EditorConfig*.

![Configurare e imporre convenzioni di scrittura del codice con EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

## <a name="debugging"></a>Debug

[Documentazione: Debug in Visual Studio](../debugger/index.md)

Visual Studio include un debugger all'avanguardia che consente di eseguire il debug delle applicazioni .NET destinate a .NET Framework, .NET Standard e .NET Core. Il debugger consente di attivare, disattivare e impostare punti di interruzione condizionali (**F9**), eseguire istruzioni di chiamate di metodi, valutare espressioni LINQ e lambda, impostare espressioni di controllo per le variabili, ricollegarsi ai processi, esaminare lo stack di chiamate e persino di apportare modifiche in tempo reale al codice durante il debug con *Modifica e continuazione*.

Se il servizio è in esecuzione in Azure, con Visual Studio 2017 Enterprise è possibile usare *Debug snapshot* per diagnosticare eventuali problemi nelle applicazioni cloud distribuite live.

![Debug in Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

## <a name="version-control"></a>Controllo della versione

[Documentazione: Controllo della versione in Visual Studio](/vsts/index)

Usare Git o il controllo della versione di Team Foundation per archiviare e aggiornare il codice in Visual Studio. All'interno dell'editor, è possibile organizzare le modifiche locali con Team Explorer e usare la barra di stato per tenere traccia di commit e modifiche in sospeso. È anche possibile configurare l'integrazione e il recapito continui all'interno di Visual Studio con l'estensione [Strumenti di recapito continuo per Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) per adottare il flusso di lavoro di sviluppo agile.

![Controllo del codice sorgente in Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

## <a name="extensibility"></a>Estendibilità

[Documentazione: Estensione di Visual Studio](../extensibility/index.md)

Visual Studio offre un ampio ecosistema di estensioni che è possibile installare o creare quando necessario. Installare le estensioni dalla *raccolta estensioni* o da *Visual Studio Marketplace*, compilare un plug-in personalizzato dell'editor con *VS SDK* o creare un analizzatore di codice o un refactoring in tempo reale personalizzato tramite *.NET Compiler Platform SDK*. È possibile trovare suggerimenti e correzioni di codice aggiuntivi scaricando l'estensione [Analisi codice Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

![Raccolta estensioni di Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")

## <a name="popular-extensions--shortcuts"></a>Estensioni e collegamenti più diffusi

Se fino a questo momento si è usato un altro ambiente IDE o di stesura di codice, può essere utile installare una di queste estensioni:

- [Emulazione Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation )
- [HotKeys per Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Di seguito sono riportate alcune combinazioni di tasti di scelta rapida comuni di Visual Studio. Si noti che alcune estensioni annullano le combinazioni di tasti di scelta rapida: per usare i comandi riportati in seguito, è necessario ripristinarle. Per ripristinare i tasti di scelta rapida per le impostazioni predefinite di Visual Studio, passare a **Strumenti > Importa/Esporta impostazioni > Reimposta tutte le impostazioni**.

| Tasti di scelta rapida (tutti i profili) | Comando | Descrizione |
|-|-|-|
| **Ctrl+T** | Vai a tutti | Consente di passare a qualsiasi dichiarazione di file/tipo/membro/simbolo |
| **F12** (o **Ctrl + clic**) | Vai a definizione | Consente di passare al punto in cui si trova la definizione di un simbolo |
| **Ctrl+F12** | Vai all'implementazione | Consente di passare da un tipo o membro di base alle varie implementazioni di questo. |
| **Maiusc+F12** | Trova tutti i riferimenti | Consente di visualizzare tutti i riferimenti di simboli o valori letterali |
| **Ctrl+.** (o **Alt+Enter** in Profilo C#) | Azioni rapide e refactoring | Visualizza le correzioni e le azioni di generazione di codice, i refactoring e altre azioni rapide disponibili in corrispondenza della posizione del cursore o del codice selezionato |
| **CTRL**+**E**,**V** | Duplicare una riga | Duplica la riga di codice in cui si trova il cursore (disponibile in **Visual Studio 2017 versione 15.6 Preview 2** e versioni successive) |
| **CTRL**+**W** | Espandere la selezione | Espande la selezione corrente di un'unità strutturale (disponibile in **Visual Studio 2017 versione 15.5**) |
| **CTRL**+**MAIUSC**+**W** | Comprimere la selezione | Comprime (riduce) la selezione corrente di un'unità strutturale (disponibile in **Visual Studio 2017 versione 15.5**) |
| **Ctrl+Q** | Avvio veloce | Consente di effettuare una ricerca all'interno di tutte le impostazioni di Visual Studio |
| **F5** | Avvia debug | Avvia il debug dell'applicazione |
| **Ctrl+F5** | Esecuzione senza debug | Esegue l'applicazione in locale senza debug |
| **Ctrl+K,D** (profilo predefinito) o **Ctrl+E,D** (profilo C#) | Formatta documento | Corregge le violazioni alle regole di formattazione nel file in base alle impostazioni relative alle nuove righe, alla spaziatura e ai rientri |
| **CTRL+\\,E** (profilo predefinito) o **CTRL+W,E** (profilo C#) | Visualizzazione dell'elenco errori | Consente di visualizzare tutti gli errori nel documento, nel progetto o nella soluzione |