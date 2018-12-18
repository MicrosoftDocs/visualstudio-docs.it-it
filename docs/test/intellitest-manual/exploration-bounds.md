---
title: Limiti di esplorazione | Strumento di test per sviluppatori Microsoft IntelliTest | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Exploration bounds
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 6ddcaaac8d814b1f77351a54de121eb641e7fe49
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="exploration-bounds"></a>Limiti di esplorazione

**PexSettingsAttributeBase** è la classe di base astratta per l'impostazione dei limiti come attributi. Vedere [Impostazioni a cascata](settings-waterfall.md) per una panoramica delle impostazioni di IntelliTest.

È possibile modificare le impostazioni usando le proprietà denominate di questo attributo e i suoi derivati:

```
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Limiti della risoluzione di vincoli**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime): numero di secondi che il [risolutore di vincoli](input-generation.md#constraint-solver) ha a disposizione per individuare gli input che fanno sì che venga seguito un nuovo e diverso percorso di esecuzione.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory): dimensione in megabyte che il [risolutore di vincoli](input-generation.md#constraint-solver) può usare per individuare gli input.<p />
* **Limiti del percorso di esplorazione**
  * [MaxBranches](#maxbranches): numero massimo di diramazioni che si possono includere in un percorso di esecuzione singola.
  * [MaxCalls](#maxcalls): numero massimo di chiamate che si possono effettuare durante un percorso di esecuzione singola.
  * [MaxStack](#maxstack): dimensione massima dello stack in qualsiasi momento durante un percorso di esecuzione singola, misurata come numero di frame di chiamata attivi.
  * [MaxConditions](#maxconditions): numero massimo di condizioni sugli input che possono essere controllati durante un percorso di esecuzione singola.<p />
* **Limiti di esplorazione**
  * [MaxRuns](#maxruns): numero massimo di esecuzioni che verranno tentate durante un'esplorazione.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests): numero massimo di esecuzioni consecutive senza che venga generato un nuovo test.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths): numero massimo di esecuzioni con percorsi di esecuzione singola che verranno tentate durante un'esplorazione.
  * [MaxExceptions](#maxexceptions): numero massimo di eccezioni che si possono trovare per una combinazione di tutti i percorsi di esecuzione individuati.<p />
* **Impostazioni di generazione di codice per il gruppo di test**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded): se è true, i percorsi di esecuzione che superano uno dei limiti di percorso ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions)) vengono ignorati.
  * [TestEmissionFilter](#testemissionfilter): indica in quali circostanze IntelliTest deve creare i test.
  * [TestEmissionBranchHits](#testemissionbranchhits): controlla il numero di test creati da IntelliTest.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Numero di secondi che il [risolutore di vincoli](input-generation.md#constraint-solver) ha a disposizione per calcolare gli input che determinano l'uso di un nuovo e diverso percorso di esecuzione. Si tratta di un'opzione di **PexSettingsAttributeBase** e i relativi tipi derivati.

Maggiore è la profondità dell'esplorazione di IntelliTest nei percorsi di esecuzione di un programma, più complessi sono i sistemi di vincoli creati da IntelliTest dal flusso di controllo e dal flusso di dati del programma. In base alla limitazione del tempo, è possibile impostare questo valore in modo da consentire a IntelliTest di dedicare più o meno tempo all'individuazione dei nuovi percorsi di esecuzione.

In genere, il timeout è dovuto al fatto che IntelliTest sta tentando di trovare una soluzione per un sistema di vincoli che non ha una soluzione, ma non è in grado di rilevare questo fatto. Poiché questo è il caso più comune di timeout, può non avere senso aumentare il limite.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

Numero di megabyte che il [risolutore di vincoli](input-generation.md#constraint-solver) ha a disposizione per calcolare gli input che determinano l'uso di un nuovo e diverso percorso di esecuzione. Si tratta di un'opzione di **PexSettingsAttributeBase** e i relativi tipi derivati.

Maggiore è la profondità dell'esplorazione di IntelliTest nei percorsi di esecuzione di un programma, più complessi sono i sistemi di vincoli creati da IntelliTest dal flusso di controllo e dal flusso di dati del programma. In base alla memoria disponibile nel computer, è possibile impostare questo valore in modo da consentire a IntelliTest di affrontare i sistemi di vincolo più complessi.

In genere, il timeout è dovuto al fatto che IntelliTest sta tentando di trovare una soluzione per un sistema di vincoli che non ha una soluzione, ma non è in grado di rilevare questo fatto. Poiché questa è la causa più comune di una situazione di memoria insufficiente, può non avere senso aumentare il limite.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Numero massimo di diramazioni che si possono includere in un percorso di esecuzione singola.

La motivazione alla base di questo limite di esplorazione è limitare la lunghezza di qualsiasi percorso di esecuzione che IntelliTest esplora durante la [generazione di input](input-generation.md). In particolare, evita che IntelliTest smetta di rispondere se il programma entra in un ciclo infinito.

Ogni diramazione condizionale e non condizionale del codice eseguito e monitorato viene conteggiata in base a questo limite, incluse le diramazioni che non dipendono dagli input del test con parametri.

Ad esempio, il codice seguente usa le diramazioni nell'ordine di 100:

```
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Numero massimo di chiamate che si possono effettuare durante un percorso di esecuzione singola.

La motivazione alla base di questo limite di esplorazione è limitare la lunghezza di qualsiasi percorso di esecuzione che IntelliTest esplora durante la [generazione di input](input-generation.md). In particolare, evita che IntelliTest smetta di rispondere se il programma chiama un metodo in modo ricorsivo un numero infinito di volte, causando un overflow dello stack che IntelliTest può non essere in grado di gestire.

Ogni chiamata (diretta, indiretta, virtuale, collegamento) del codice eseguito e monitorato viene conteggiata in base a questo limite.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Dimensione massima dello stack in qualsiasi momento durante un percorso di esecuzione singola, misurata in base al numero di frame di chiamata attivi.

La motivazione alla base di questo limite di esplorazione è limitare la dimensione dello stack di qualsiasi percorso di esecuzione che IntelliTest esplora durante la [generazione di input](input-generation.md). In particolare, evita che IntelliTest usi tutto lo spazio disponibile nello stack, causando un overflow dello stack che IntelliTest può non essere in grado di gestire.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Numero massimo di condizioni sugli input che possono essere controllati durante un percorso di esecuzione singola.

La motivazione alla base di questo limite di esplorazione è limitare la complessità di qualsiasi percorso di esecuzione che IntelliTest esplora durante la [generazione di input](input-generation.md). Ogni diramazione condizionale che dipende dagli input del test con parametri viene conteggiata in base a questo limite.

Ad esempio, ogni percorso nel codice seguente usa n+1 condizioni:

```
[PexMethod]
void ParameterizedTest(int n) 
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

Numero massimo di esecuzioni che IntelliTest tenterà durante l'esplorazione di un test.

La motivazione alla base di questo limite di esplorazione è che qualsiasi codice che contiene cicli o ricorsioni potrebbe avere un numero infinito di percorsi di esecuzione, quindi IntelliTest deve essere limitato durante la [generazione di input](input-generation.md). 

Le due impostazioni **MaxRuns** e **MaxRunsWithUniquePaths** sono correlate nel modo seguente: 

* IntelliTest chiamerà un metodo di test con parametri al massimo **MaxRuns** volte con input di test diversi.
* Se il codice eseguito è deterministico, IntelliTest userà un percorso di esecuzione diverso ogni volta. 
  Tuttavia, in alcune condizioni il codice eseguito può seguire un percorso di esecuzione già usato in precedenza, con input diversi. 
* IntelliTest conta i percorsi di esecuzione univoca che trova: questo numero è limitato dall'opzione **MaxRunsWithUniquePaths**.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Numero massimo di esecuzioni consecutive senza che venga generato un nuovo test.

Benché IntelliTest spesso sia in grado di individuare rapidamente molti input di test interessanti, dopo un certo tempo non trova più nuovi input di test e non genera altri unit test. Questa opzione di configurazione definisce un limite per il numero di tentativi consecutivi che IntellTtest può effettuare senza creare un nuovo test. Raggiunto il limite, l'esplorazione viene interrotta. 

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Numero massimo di percorsi univoci che IntelliTest prenderà in considerazione durante un'esplorazione.

La motivazione alla base di questo limite di esplorazione è che qualsiasi codice che contiene cicli o ricorsioni potrebbe avere un numero infinito di percorsi di esecuzione, quindi IntelliTest deve essere limitato durante la [generazione di input](input-generation.md).

Le due impostazioni **MaxRuns** e **MaxRunsWithUniquePaths** sono correlate nel modo seguente: 

* IntelliTest chiamerà un metodo di test con parametri al massimo **MaxRuns** volte con input di test diversi.
* Se il codice eseguito è deterministico, IntelliTest userà un percorso di esecuzione diverso ogni volta. 
  Tuttavia, in alcune condizioni il codice eseguito può seguire un percorso di esecuzione già usato in precedenza, con input diversi. 
* IntelliTest conta i percorsi di esecuzione univoca che trova: questo numero è limitato dall'opzione **MaxRunsWithUniquePaths**.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Numero massimo di eccezioni che possono essere rilevate prima che l'esplorazione venga interrotta.

La motivazione alla base di questo limite di esplorazione è interrompere l'esplorazione del codice che contiene molti bug.
Se IntelliTest trova troppi errori nel codice, l'esplorazione si arresta.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

I percorsi di esecuzione che superano i limiti di percorso configurati, [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack) e [MaxConditions](#maxconditions), vengono ignorati.

La motivazione alla base di questo limite di esplorazione è gestire i test potenzialmente non terminati. Quando IntelliTest raggiunge un limite di esplorazione come [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack) o [MaxConditions](#maxconditions), presuppone che il test non sarà un processo non terminato e non causerà un overflow dello stack in un secondo momento.
Questi test case possono causare problemi agli altri framework di test e questo attributo consente di impedire a IntelliTest di generare test case per i processi potenzialmente non terminati oppure test case che causeranno un overflow dello stack.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Indica i tipi di test che devono essere creati da IntelliTest. I valori possibili sono:

* **All**: vengono generati test per qualsiasi attività, incluse le violazioni delle assunzioni.
* **FailuresAndIncreasedBranchHits** (impostazione predefinita): vengono generati test per tutti gli errori univoci e ogni volta che un test case incrementa il code coverage, in base al controllo di [TestEmissionBranchHits](#testemissionbranchhits).
* **FailuresAndUniquePaths**: vengono generati test per tutti gli errori rilevati da IntelliTest e per ogni input di test che comporta un percorso di esecuzione univoca.
* **Failures**: vengono generati test solo per gli errori.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

In base all'impostazione corrente di [TestEmissionFilter](#testemissionfilter), IntelliTest genera nuovi test case quando riguardano una diramazione del programma che non è stata analizzata in precedenza.

L'impostazione **TestEmissionBranchHits** determina se IntelliTest deve solo considerare se una diramazione è stata analizzata (**TestEmissionBranchHits = 1**), se un test ha eseguito l'analisi una o due volte (**TestEmissionBranchHits = 2**) e così via.

**TestEmissionBranchHits = 1** produce un gruppo di test molto piccolo che esamina tutte le diramazioni che IntelliTest è in grado di raggiungere. In particolare, questo gruppo di test esamina anche tutti i blocchi di base e le istruzioni che raggiunge. 

Il valore predefinito per questa opzione è **TestEmissionBranchHits=2**, che genera un gruppo di test più espressivo e più adatto per rilevare i futuri errori di regressione.

## <a name="got-feedback"></a>Commenti?

Pubblicare idee e richieste di funzionalità in **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
