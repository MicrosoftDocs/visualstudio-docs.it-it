---
title: Avvisi ed errori | Strumento di test per sviluppatori Microsoft IntelliTest | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Warnings and errors
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 77f47c2d18b43c3ab08dac5fec6281892072ab36
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="warnings-and-errors"></a>Avvisi ed errori

## <a name="warnings-and-errors-by-category"></a>Avvisi ed errori per categoria

* **Limiti**
  * [MaxBranches superato](#maxbranches-exceeded)
  * [MaxConstraintSolverTime superato](#maxconstraintsolvertime-exceeded)
  * [MaxConditions superato](#maxconditions-exceeded)
  * [MaxCalls superato](#maxcalls-exceeded)
  * [MaxStack superato](#maxstack-exceeded)
  * [MaxRuns superato](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests superato](#maxrunswithoutnewtests-exceeded)<p />

* **Risoluzione di vincoli**
  * [Non è possibile concretizzare la soluzione](#cannot-concretize-solution)<p />

* **Domini**
  * [Serve aiuto per costruire l'oggetto](#help-construct)
  * [Serve aiuto per trovare i tipi](#help-types)
  * [Tipo utilizzabile ipotizzato](#usable-type-guessed)<p />

* **Esecuzione**
  * [Errore imprevisto nell'esplorazione](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)<p />

* **Strumentazione**
  * [Chiamata di metodo non instrumentato](#uninstrumented-method-called)
  * [Chiamata di metodo esterno](#external-method-called)
  * [Chiamata di metodo non instrumentabile](#uninstrumentable-method-called)
  * [Problema di testabilità](#testability-issue)
  * [Limitazione](#limitation)<p />

* **Interprete**
  * [Rilevata mancata corrispondenza della chiamata](#observed-call-mismatch)
  * [Valore memorizzato in un campo statico](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches superato

IntelliTest limita la lunghezza dei percorsi di esecuzione che esplora durante la [generazione dell'input](input-generation.md). Questa funzionalità evita che IntelliTest smetta di rispondere quando il programma entra in un ciclo infinito.

Ogni diramazione condizionale e non condizionale del codice eseguito e monitorato viene conteggiata in base a questo limite, incluse le diramazioni che non dipendono dagli input dello [unit test con parametri](test-generation.md#parameterized-unit-testing).

Ad esempio, il codice seguente usa le diramazioni nell'ordine di 100:

```
for (int i=0; i<100; i++) { }
```

È possibile modificare l'opzione **MaxBranches** di un attributo derivato da **PexSettingsAttributeBase**, ad esempio [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). Nell'esempio seguente questo limite viene rimosso in modo efficace:

```
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

È anche possibile impostare l'opzione **TestExcludePathBoundsExceeded** per indicare a IntelliTest come gestire in genere questi problemi.

Nel codice di test è possibile usare [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) per ignorare i vincoli generati dalla condizione di ciclo:

```
for (int i=0; 
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++) 
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime superato

IntelliTest usa un [risolutore di vincoli](input-generation.md#constraint-solver) per calcolare nuovi input di test. Il processo di risoluzione dei vincoli può richiedere molto tempo. Pertanto, IntelliTest consente di configurare limiti, in particolare **MaxConstraintSolverTime**.

Per molte applicazioni, l'aumento significativo del timeout non determinerà un code coverage migliore. Il motivo è che la maggior parte dei timeout sono causati da sistemi di vincoli per i quali non esistono soluzioni. Tuttavia, IntelliTest potrebbe non riuscire a stabilire l'incoerenza senza prima provare tutte le possibili soluzioni, determinando un timeout.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions superato

IntelliTest limita la lunghezza dei percorsi di esecuzione che esplora durante la [generazione dell'input](input-generation.md). Questa funzionalità evita che IntelliTest smetta di rispondere quando il programma entra in un ciclo infinito.

Ogni diramazione condizionale che dipende dagli input dello [unit test con parametri](test-generation.md#parameterized-unit-testing) viene conteggiata in base a questo limite.

Ad esempio, ogni percorso nel codice seguente usa **n + 1** condizioni:

```
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++) 
    { ... }
}
```

È possibile modificare l'opzione **MaxConditions** di un attributo derivato da **PexSettingsAttributeBase**, ad esempio [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). Ad esempio:

```
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

È anche possibile impostare l'opzione **TestExcludePathBoundsExceeded** per indicare a IntelliTest come gestire in genere questi problemi.

È possibile usare [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) per ignorare i vincoli generati dalla condizione di ciclo:

```
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)  
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>MaxCalls superato

IntelliTest limita la lunghezza dei percorsi di esecuzione che esplora durante la [generazione dell'input](input-generation.md). Questa funzionalità evita che IntelliTest smetta di rispondere quando il programma entra in un ciclo infinito.

Ogni chiamata (diretta, indiretta, virtuale o collegamento) del codice eseguito e monitorato viene conteggiata in base a questo limite.

È possibile modificare l'opzione **MaxCalls** di un attributo derivato da **PexSettingsAttributeBase**, ad esempio [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). Nell'esempio seguente questo limite viene rimosso in modo efficace:

```
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

È anche possibile impostare l'opzione **TestExcludePathBoundsExceeded** per indicare a IntelliTest come gestire in genere questi problemi.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack superato

IntelliTest limita la dimensione dello stack di chiamate dei percorsi di esecuzione che esplora durante la [generazione dell'input](input-generation.md). Questa funzionalità evita che IntelliTest venga terminato quando si verifica un overflow dello stack.

È possibile modificare l'opzione **MaxStack** di un attributo derivato da **PexSettingsAttributeBase**, ad esempio [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). Nell'esempio seguente questo limite viene rimosso in modo efficace (scelta non consigliata):

```
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

È anche possibile impostare l'opzione **TestExcludePathBoundsExceeded** per indicare a IntelliTest come gestire in genere questi problemi.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns superato

IntelliTest limita il numero dei percorsi di esecuzione che esplora durante la [generazione dell'input](input-generation.md). Questa funzionalità assicura che IntelliTest venga terminato quando il programma entra in un ciclo o in una ricorsione.

È possibile che IntelliTest non generi un nuovo test case a ogni esecuzione del test con parametri mediante l'uso di particolari input. Per altre informazioni, vedere [TestEmissionFilter](exploration-bounds.md#testemissionfilter).

È possibile modificare l'opzione **MaxRuns** di un attributo derivato da **PexSettingsAttributeBase**, ad esempio [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). Nell'esempio seguente questo limite viene rimosso in modo efficace (scelta non consigliata):

```
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests superato

IntelliTest limita il numero dei percorsi di esecuzione che esplora durante la [generazione dell'input](input-generation.md). Questa funzionalità assicura che IntelliTest venga terminato quando il programma entra in un ciclo o in una ricorsione.

È possibile che IntelliTest non generi un nuovo test case a ogni esecuzione del test con parametri mediante l'uso di particolari input. Per altre informazioni, vedere [TestEmissionFilter](exploration-bounds.md#testemissionfilter).

Sebbene inizialmente IntelliTest riesca spesso a individuare molti input di test interessanti, con il passare del tempo potrebbe non generare altri test. Questa opzione determina per quanto tempo IntelliTest può tentare di trovare un altro input di test pertinente.

È possibile modificare l'opzione **MaxRunsWithoutNewTests** di un attributo derivato da **PexSettingsAttributeBase**, ad esempio [PexClass](attribute-glossary.md#pexclass) o [PexMethod](attribute-glossary.md#pexmethod). Nell'esempio seguente questo limite viene rimosso in modo efficace (scelta non consigliata):

```
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Non è possibile concretizzare la soluzione

Questo errore è spesso la conseguenza di un errore precedente. IntelliTest usa un [risolutore di vincoli](input-generation.md#constraint-solver) per determinare nuovi input di test. In alcuni casi, gli input di test proposti dal [risolutore di vincoli](input-generation.md#constraint-solver) non sono validi. Questa situazione può verificarsi quando:

* alcuni vincoli non sono noti
* i valori vengono creati in modo definito dall'utente, causando errori nel codice utente
* la logica di inizializzazione di alcuni dei tipi interessati non è controllata da IntelliTest (ad esempio, le classi COM)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Serve aiuto per costruire l'oggetto

IntelliTest [genera input di test](input-generation.md) e alcuni input possono essere oggetti che includono campi. In questo caso, IntelliTest prova a generare un'istanza di una classe con un campo privato e presuppone che si verificherà un comportamento interessante del programma quando questo campo privato ha un particolare valore. 

Tuttavia, sebbene ciò sia possibile con la reflection, IntelliTest non produce oggetti con valori di campo arbitrari. In questi casi si basa invece sui suggerimenti dell'utente relativamente all'uso dei metodi pubblici di una classe per creare un oggetto e portarlo in uno stato in cui il relativo campo privato abbia il valore desiderato.

Leggere [Creazione di istanze di classi esistenti](input-generation.md#existing-classes) per informazioni su come aiutare IntelliTest a costruire oggetti interessanti. 

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Serve aiuto per trovare i tipi

IntelliTest [genera input di test](input-generation.md) per qualsiasi tipo .NET. In questo caso IntelliTest tenta di creare un'istanza che deriva da una classe astratta o implementa un'interfaccia astratta e nessun tipo che soddisfi i vincoli è noto a IntelliTest. 

È possibile aiutare IntelliTest puntando a uno o più tipi che corrispondano ai vincoli. Uno degli attributi seguenti è in genere utile:

* **PexUseTypeAttribute**, che punta a un tipo particolare.

  Se ad esempio IntelliTest segnala di "non conoscere tipi assegnabili a **System.Collections.IDictionary**", è possibile aggiungere l'attributo **PexUseTypeAttribute** seguente al test (o alla classe della fixture):

  ```
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Un attributo a livello di assembly**

  ```
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Tipo utilizzabile ipotizzato

IntelliTest [genera input di test](input-generation.md) per qualsiasi tipo .NET. Quando un tipo è astratto o è un'interfaccia, IntelliTest deve scegliere una particolare implementazione del tipo. Per effettuare questa scelta, deve conoscere i tipi esistenti. 

La visualizzazione di questo avviso indica che IntelliTest ha esaminato alcune delle assembly di riferimento e ha trovato un tipo di implementazione, ma non ha indicazioni in merito all'uso di questo tipo o di tipi più appropriati che potrebbero essere disponibili altrove. IntelliTest ha semplicemente scelto un tipo che sembrava promettente.

Per evitare questo avviso, è possibile accettare la scelta di IntelliTest o indicare a IntelliTest di usare altri tipi aggiungendo un attributo [PexUseType](attribute-glossary.md#pexusetype) corrispondente.

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Errore imprevisto nell'esplorazione

Durante l'esplorazione di un test è stata rilevata un'eccezione imprevista.

[Segnalarla come un bug](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

È stata rilevata un'eccezione nel codice utente. Ispezionare l'analisi dello stack e rimuovere il bug nel codice.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Chiamata di metodo non instrumentato

IntelliTest [genera input di test](input-generation.md) monitorando l'esecuzione del programma. È fondamentale che il codice pertinente sia instrumentato correttamente in modo che IntelliTest possa monitorarne il comportamento.

Questo avviso viene visualizzato quando il codice instrumentato chiama i metodi in un altro assembly non instrumentato. Se si desidera che IntelliTest esplori l'interazione di entrambi, è necessario instrumentare anche l'altro assembly (o parti di esso).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Chiamata di metodo esterno

IntelliTest [genera input di test](input-generation.md) monitorando l'esecuzione delle applicazioni .NET. IntelliTest non è in grado di generare input di test significativi per il codice non scritto in un linguaggio .NET.

Questo avviso viene visualizzato quando il codice instrumentato chiama un metodo nativo non gestito che IntelliTest non può analizzare. Se si desidera che IntelliTest esplori l'interazione di entrambi, è necessario simulare il metodo non gestito.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Chiamata di metodo non instrumentabile

IntelliTest [genera input di test](input-generation.md) monitorando l'esecuzione delle applicazioni .NET. Tuttavia, esistono alcuni metodi che, per motivi tecnici, IntelliTest non è in grado di monitorare. IntelliTest non può ad esempio monitorare un costruttore statico.

Questo avviso viene visualizzato quando il codice instrumentato chiama un metodo che IntelliTest non può monitorare. 

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Problema di testabilità

IntelliTest [genera input di test](input-generation.md) monitorando l'esecuzione del programma ed è in grado di generare input di test pertinenti solo quando il programma è deterministico e il comportamento attinente è controllato dagli input di test.

Questo avviso viene visualizzato perché durante l'esecuzione del test case è stato chiamato un metodo che si comporta in modo non deterministico o interagisce con l'ambiente. Esempi sono i metodi di **System.Random** e **System.IO.File**. Se si desidera che IntelliTest crei input di test significativi, è necessario simulare i metodi che IntelliTest contrassegna come problemi di testabilità.

<a name="limitation"></a>
## <a name="limitation"></a>Limitazione

IntelliTest [genera input di test](input-generation.md) usando un [risolutore di vincoli](input-generation.md#constraint-solver).
Tuttavia, alcune operazioni non rientrano nell'ambito del [risolutore di vincoli](input-generation.md#constraint-solver).
Queste attualmente includono:

* la maggior parte delle operazioni a virgola mobile (sono supportate solo alcune operazioni aritmetiche lineari sui numeri a virgola mobile)
* conversioni tra numeri a virgola mobile e interi
* tutte le operazioni sul tipo **System.Decimal**

Questo avviso viene visualizzato quando il codice eseguito effettua un'operazione o chiama un metodo che IntelliTest non è in grado di interpretare. 

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Rilevata mancata corrispondenza della chiamata

IntelliTest [genera input di test](input-generation.md) monitorando l'esecuzione del programma. Tuttavia, IntelliTest potrebbe non essere in grado di monitorare tutte le istruzioni. Non può ad esempio monitorare il codice nativo e il codice non instrumentato.

Quando IntelliTest non può monitorare il codice, non sarà in grado di generare gli input di test pertinenti al codice.
Spesso l'impossibilità di monitorare un metodo diventa nota a IntelliTest solo dopo che una chiamata al metodo viene restituita. Tuttavia, la causa di questo avviso è:

* IntelliTest ha monitorato del codice determinando l'avvio di una chiamata a un metodo non instrumentato
* Il metodo non instrumentato ha chiamato un metodo instrumentato
* IntelliTest monitora il metodo instrumentato che è stato chiamato 

IntelliTest non conosce le operazioni eseguite dal metodo intermedio non instrumentato e potrebbe quindi non essere in grado di generare input di test pertinenti alla chiamata instrumentata annidata.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Valore memorizzato in un campo statico

IntelliTest è in grado di determinare in modo sistematico [input di test pertinenti](input-generation.md) solo quando lo unit test è deterministico. In altre parole, si comporta sempre allo stesso modo per gli stessi input di test. In particolare, ciò significa che il test deve lasciare il sistema in uno stato che consenta di eseguire nuovamente il test.
È preferibile che lo unit test non modifichi lo stato globale, ma tutte le interazioni con elementi globali devono essere fittizie.

Questo avviso indica che un campo statico è stato modificato. Ciò potrebbe causare un comportamento del test non deterministico.

In alcuni casi la modifica di un campo statico è accettabile:

* quando gli input di test determinano l'annullamento della modifica da parte del codice di installazione o di pulizia
* quando il campo viene avviato una sola volta e il valore non viene successivamente modificato

<a name="report-bug"></a>

## <a name="got-feedback"></a>Commenti?

Pubblicare idee e richieste di funzionalità in **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
