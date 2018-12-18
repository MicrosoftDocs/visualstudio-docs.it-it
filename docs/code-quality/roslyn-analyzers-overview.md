---
title: Analizzatori di Roslyn in Visual Studio
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: f5a434a47bac73aef86e83d220605b196fc2a74a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Panoramica di analizzatori .NET Compiler Platform

Visual Studio 2017 include un set predefinito di analizzatori .NET Compiler Platform che consentono di analizzare il codice c# o Visual Basic durante la digitazione. È possibile installare gli analizzatori aggiuntivi come un'estensione di Visual Studio o in base al progetto come pacchetto NuGet. Gli analizzatori osservare stile code, qualità del codice e manutenibilità, progettazione di codice e altri problemi.

Se vengono rilevate violazioni della regola da un analizzatore, vengono segnalati entrambi nell'editor di codice come un *ondulate* sotto il codice che e nel **elenco errori**.

Molte regole analizzatore, o *diagnostica*, con uno o più associata *correzioni del codice* che è possibile applicare per risolvere il problema. Gli strumenti di diagnostica analizzatore sono integrate in Visual Studio hanno una correzione del codice associato. Le correzioni del codice vengono visualizzate nel menu insieme ad altri tipi di icona lampadina *azioni rapide*. Per informazioni su queste correzioni del codice, vedere [comuni azioni rapide](../ide/common-quick-actions.md).

![Violazione di analizzatore e correzione del codice azione rapida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analizzatori di Roslyn e analisi statica del codice

Gli analizzatori di .NET compiler Platform ("Roslyn") sostituirà [analisi statica del codice](../code-quality/code-analysis-for-managed-code-overview.md) per il codice gestito. Molte delle regole di analisi statica del codice sono già state riscritte come diagnostica analyzer Roslyn.

Come delle violazioni delle regole analisi statica del codice, le violazioni di Analizzatore Roslyn vengono visualizzati nel **elenco errori**. Inoltre, le violazioni di Analizzatore Roslyn inoltre visualizzata nell'editor di codice come *ondulate* sotto il codice che causa l'errore. Il colore dell'ondulate dipende il [impostazione di gravità](../code-quality/use-roslyn-analyzers.md#rule-severity) della regola. La seguente schermata Mostra violazioni di tre&mdash;uno rosso, uno verde e uno grigio:

![Linee ondulate nell'editor di codice](media/diagnostics-severity-colors.png)

Gli analizzatori di Roslyn analisi del codice in fase di compilazione, ad esempio di analisi statica del codice se è abilitata, ma anche in tempo reale durante la digitazione. Analizzatori Roslyn possono anche fornire analisi in fase di progettazione di file di codice che non sono aperti nell'editor se si abilita [analisi della soluzione completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Fase di compilazione errori e avvisi da analizzatori Roslyn vengono visualizzati solo se gli analizzatori vengono installati come pacchetto NuGet.

Non solo eseguire gli analizzatori Roslyn segnalano gli stessi tipi di problemi di analisi statica del codice, ma semplificano le operazioni per la correzione di una o tutte le occorrenze della violazione in un progetto o al file. Queste azioni vengono chiamate *correzioni del codice*. Le correzioni del codice sono specifici dell'IDE; in Visual Studio, vengono implementate come [azioni rapide](../ide/quick-actions.md). Non tutti i dati diagnostici analizzatore hanno una correzione del codice associato.

> [!NOTE]
> L'opzione di menu **Analizza** > **Esegui analisi del codice** si applica l'analisi del codice solo su static. Inoltre, in un progetto **analisi del codice** pagina delle proprietà, la **Attiva analisi codice in fase di compilazione** e **Elimina i risultati dal codice generato** caselle di controllo si applicano solo a analisi statica del codice. Non hanno effetto su analizzatori Roslyn.

Per differenziare le violazioni da Roslyn analizzatori e analisi statica del codice nel **elenco errori**, esaminare i **strumento** colonna. Se il valore di strumento corrispondente a uno degli assembly nell'analizzatore **Esplora soluzioni**, ad esempio **Microsoft.CodeQuality.Analyzers**, la violazione proviene da uno strumento di analisi Roslyn. In caso contrario, la violazione deriva dall'analisi statica del codice.

![Colonna strumento nell'elenco errori](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-vs-extension"></a>Pacchetto NuGet e di estensione

.NET compiler Platform gli analizzatori possono essere installati per ogni progetto tramite un pacchetto NuGet o un livello di Visual Studio come estensione di Visual Studio. Esistono alcune differenze di comportamento del tasto tra questi due metodi [installazione analizzatori](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ambito

Se si installano gli analizzatori come estensione di Visual Studio, si applicano a livello di soluzione, a tutte le istanze di Visual Studio. Se si installano gli analizzatori come pacchetto NuGet, ovvero il metodo preferito, si applicano solo al progetto in cui è stato installato il pacchetto NuGet. Negli ambienti di team, rientrano nell'ambito per gli analizzatori installati come pacchetti NuGet *tutti gli sviluppatori* che funzionano sul progetto.

### <a name="build-errors"></a>Errori di compilazione

Per avere regole applicate in fase di compilazione, tra cui tramite la riga di comando o come parte di un'integrazione continua (CI) compilazione, installare gli analizzatori come pacchetto NuGet. Errori e avvisi analizzatore non vengono visualizzati nel report di compilazione se si installano gli analizzatori come estensione.

La schermata seguente mostra l'output di compilazione da riga di comando di compilazione di un progetto che contiene una violazione delle regole di Analizzatore:

![Output di MSBuild con violazione delle regole](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravità regola

È possibile impostare il livello di gravità di regole da analizzatori che sono stati installati come un'estensione di Visual Studio. Per configurare [regola gravità](../code-quality/use-roslyn-analyzers.md#rule-severity), installare gli analizzatori come pacchetto NuGet.

## <a name="next-steps"></a>Passaggi successivi

- [Installare gli analizzatori di Roslyn in Visual Studio](../code-quality/install-roslyn-analyzers.md)
- [Usare gli analizzatori di Roslyn in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Azioni rapide in Visual Studio](../ide/quick-actions.md)
- [Scrivere la propria analyzer Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)