---
title: Creazione di processori di direttiva di modelli di testo T4 personalizzati
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 728fba66739bf09cfd1b4181b3347fd2994273ef
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Creazione di processori di direttiva di modelli di testo T4 personalizzati

Il *processo di trasformazione del modello testo* accetta un *modello di testo* file come input e produce un file di testo come output. Il *motore di trasformazione del modello di testo* il processo e il motore interagisce con un host di trasformazione del modello di testo e il modello di testo di uno o più controlli *processori di direttiva* per completare il processo. Per ulteriori informazioni, vedere [il processo di trasformazione di modello di testo](../modeling/the-text-template-transformation-process.md).

Per creare un processore di direttiva personalizzato, si crea una classe che eredita da <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

La differenza tra questi due è che <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementa l'interfaccia minima che è necessario recuperare parametri da parte dell'utente e per generare il codice che genera il file di output del modello. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa il modello di progettazione richiede/fornisce. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> gestisce due parametri speciali `requires` e `provides`.  Ad esempio, un processore di direttiva personalizzato potrebbe accettare un nome file dall'utente, aprire e leggere il file e quindi archiviare il testo del file in una variabile denominata `fileText`. Una sottoclasse del <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> classe potrebbe richiedere un nome di file da parte dell'utente come valore della `requires` parametro e il nome della variabile in cui archiviare il testo come valore della `provides` parametro. Questo processore verrebbe aprire e leggere il file e quindi archiviare il testo del file nella variabile specificata.

Prima di chiamare un processore di direttiva personalizzato da un modello di testo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è necessario registrarlo.

Per ulteriori informazioni su come aggiungere la chiave del Registro di sistema, vedere [distribuzione di un processore di direttiva personalizzato](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Direttive personalizzate

Una direttiva personalizzata è simile al seguente:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

È possibile utilizzare un processore di direttiva personalizzato quando si desidera accedere alle risorse o dati esterni da un modello di testo.

Modelli di testo diversi possono condividere la funzionalità che fornisce un singolo processore di direttiva, pertanto i processori di direttiva forniscono un modo per scomporre il codice per il riutilizzo. L'elemento predefinito `include` direttiva è simile, quanto è possibile utilizzarlo per scomporre il codice e condividerlo tra modelli di testo diversi. La differenza è che le funzionalità che la `include` fornita dalla direttiva è fisso e non accetta parametri. Se si desidera fornire funzionalità comuni a un modello di testo e consente di passare i parametri di modello, è necessario creare un processore di direttiva personalizzato.

Alcuni esempi di processori di direttiva personalizzati può essere:

-   Un processore di direttiva per restituire dati da un database che accetta un nome utente e una password come parametri.

-   Un processore di direttiva ad aprire e leggere un file che accetta il nome del file come parametro.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Parti principali di un processore di direttiva personalizzato

Per sviluppare un processore di direttiva, è necessario creare una classe che eredita da <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

La più importante `DirectiveProcessor` metodi che è necessario implementare sono i seguenti.

-   `bool IsDirectiveSupported(string directiveName)` -Restituito `true` se il processore di direttiva è possibile gestire con la direttiva denominata.

-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -Il motore del modello chiama questo metodo per ogni occorrenza di una direttiva nel modello. Il processore deve salvare i risultati.

Dopo tutte le chiamate a ProcessDirective (), il motore del modello chiamerà tali metodi:

-   `string[] GetReferencesForProcessingRun()` : Restituisce i nomi degli assembly che richiede il codice del modello.

-   `string[] GetImportsForProcessingRun()` -Restituire gli spazi dei nomi che può essere usato nel codice del modello.

-   `string GetClassCodeForProcessingRun()` : Restituisce il codice di metodi, proprietà e altre dichiarazioni che è possibile utilizzare il codice del modello. Il modo più semplice per eseguire questa operazione consiste nel compilare una stringa contenente il codice c# o Visual Basic. Affinché il processore di direttiva sia in grado di essere chiamato da un modello che utilizza un qualsiasi linguaggio CLR, è possibile creare le istruzioni come una struttura ad albero CodeDom e quindi restituire il risultato della serializzazione l'albero nella lingua utilizzata dal modello.

-   Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un processore di direttiva personalizzato](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Vedere anche

- [Distribuire un processore di direttiva personalizzato](../modeling/deploying-a-custom-directive-processor.md) viene illustrato come registrare un processore di direttiva personalizzato.
- [Procedura dettagliata: Creare un processore di direttiva personalizzato](../modeling/walkthrough-creating-a-custom-directive-processor.md) viene descritto come creare un processore di direttiva personalizzato, come registrare e testare il processore di direttiva e come formattare il file di output in formato HTML.