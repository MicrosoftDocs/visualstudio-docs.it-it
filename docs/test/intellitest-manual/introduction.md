---
title: Panoramica | Strumento di test per sviluppatori Microsoft IntelliTest | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c5e95091b9305e6802976d19570783459cc47179
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="overview-of-microsoft-intellitest"></a>Panoramica di Microsoft IntelliTest

IntelliTest consente di trovare tempestivamente i bug e riduce i costi di manutenzione dei test. Grazie a un approccio automatizzato e trasparente, IntelliTest è in grado di generare un gruppo di test candidato per il codice .NET. La generazione del gruppo di test può essere definita ulteriormente mediante la specifica di *proprietà di correttezza*. IntelliTest sviluppa anche il gruppo di test in modo automatico seguendo l'evoluzione del codice sottoposto a test.

**Test di caratterizzazione** IntelliTest consente di determinare il comportamento del codice in termini di un gruppo di unit test tradizionali.
Questo gruppo di test può essere usato come gruppo di regressione e contribuire a ridurre la complessità associata al refactoring di codice legacy o poco noto.

**Generazione guidata di input di test** IntelliTest usa un approccio di analisi del codice aperto e risoluzione vincoli per generare automaticamente valori di input di test precisi, in genere senza richiedere l'intervento dell'utente. Per i tipi di oggetto complessi genera automaticamente factory. È possibile orientare la generazione di input di test estendendo e configurando le factory per soddisfare esigenze specifiche. Anche le proprietà di correttezza specificate come asserzioni nel codice vengono usate in modo automatico per orientare ulteriormente la generazione di input di test.

**Integrazione nell'IDE** IntelliTest è completamente integrato nell'IDE di Visual Studio. Tutte le informazioni raccolte durante la generazione del gruppo di test (ad esempio gli input generati automaticamente, l'output del codice, i test case generati e il loro stato pass o fail) vengono visualizzate nell'IDE di Visual Studio. È possibile alternare facilmente tra la correzione del codice e una nuova esecuzione di IntelliTest senza chiudere l'IDE di Visual Studio.
I test possono essere salvati nella soluzione come progetto unit test e quindi vengono rilevati automaticamente da Esplora Test di Visual Studio.

**Integrare le procedure di test esistenti** È possibile usare IntelliTest per integrare le procedure di test già applicate.

Per testare:

* Algoritmi su dati primitivi o matrici di dati primitivi:
  * creare [unit test con parametri](test-generation.md#parameterized-unit-testing)
* Algoritmi su dati complessi, ad esempio dati del compilatore:
  * far generare a IntelliTest una rappresentazione astratta dei dati, quindi sottoporla all'algoritmo
  * far creare istanze a IntelliTest mediante la [creazione oggetti personalizzata](input-generation.md#objects) e gli invariant di dati, quindi chiamare l'algoritmo
* Contenitori di dati:
  * creare [unit test con parametri](test-generation.md#parameterized-unit-testing)
  * far creare istanze a IntelliTest con la [creazione oggetti personalizzata](input-generation.md#objects) e gli invariant di dati e quindi chiamare un metodo del contenitore e verificare di nuovo gli invariant in un secondo momento
  * scrivere [unit test con parametri](test-generation.md#parameterized-unit-testing) che chiamano metodi diversi dell'implementazione a seconda dei valori dei parametri
* Una codebase esistente:
  * usare la procedura guidata IntelliTest di Visual Studio per iniziare a creare un set di [unit test con parametri (PUT)](test-generation.md#parameterized-unit-testing)

## <a name="the-hello-world-of-intellitest"></a>Hello World di IntelliTest

IntelliTest trova gli input pertinenti al programma testato, pertanto è possibile usarlo per generare la famosa stringa **Hello World!** . A tale scopo è necessario aver creato un progetto di test C# basato su MSTest e avere aggiunto un riferimento **Microsoft.Pex.Framework**. Se si usa un framework di test diverso, creare una libreria di classi C# e vedere la documentazione del framework di test per informazioni sull'impostazione del progetto.

Nell'esempio seguente vengono creati due vincoli sul parametro denominato **value**, in modo che IntelliTest generi la stringa necessaria:

```csharp
using System;
using Microsoft.Pex.Framework;
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

Dopo la compilazione e l'esecuzione IntelliTest genera un set di test come il seguente:

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

Leggere [Generare unit test con IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md) per capire dove vengono salvati i test generati. Il codice di test generato deve includere un test come il seguente:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

È facile!

## <a name="limitations"></a>Limitazioni

In questa sezione vengono descritte le limitazioni di IntelliTest:

* [Non determinismo](#nondeterminism)
* [Concorrenza](#concurrency)
* [Codice .NET nativo](#native-code)
* [Piattaforma](#platform)
* [Lingua](#language)
* [Ragionamento simbolico](#symbolic-reasoning)
* [Analisi dello stack](#incorrect-stack)

### <a name="nondeterminism"></a>Non determinismo

IntelliTest presuppone che il programma analizzato sia deterministico. In caso contrario, l'esecuzione di IntelliTest viene ripetuta in ciclo fino a quando non viene raggiunto un limite di esplorazione.

IntelliTest considera un programma come non deterministico se si basa su input che IntelliTest non può controllare.

IntelliTest controlla gli input specificati a [unit test con parametri](test-generation.md#parameterized-unit-testing) e ottenuti da [PexChoose](static-helper-classes.md#pexchoose).
Anche i risultati di chiamate a codice non gestito o non instrumentato sono considerati "input" al programma instrumentato, ma IntelliTest non può controllarli. Se il flusso di controllo del programma dipende da valori specifici provenienti da tali origini esterne, IntelliTest non può "orientare" il programma verso aree non esaminate in precedenza.

Il programma è considerato non deterministico anche quando i valori provenienti da origini esterne cambiano alla successiva esecuzione del programma stesso. In questi casi IntelliTest non mantiene il controllo dell'esecuzione del programma e la ricerca diventa inefficiente.

Tali casi non sono sempre evidenti.
Considerare gli esempi seguenti:

* Il risultato del metodo **GetHashCode()** è specificato da codice non gestito e non è prevedibile.
* La classe **System.Random** usa l'ora di sistema corrente per specificare valori realmente casuali.
* La classe **System.DateTime** specifica l'ora corrente, che non è sotto il controllo di IntelliTest.

### <a name="concurrency"></a>Concorrenza

IntelliTest non gestisce programmi con multithreading.

### <a name="native-code"></a>Codice nativo

IntelliTest non riconosce il codice nativo, ad esempio le istruzioni x86 chiamate tramite **P/Invoke**. Non è in grado di tradurre le chiamate di questo tipo in vincoli che possono essere passati al [risolutore di vincoli](input-generation.md#constraint-solver).
Anche nel caso del codice .NET IntelliTest può analizzare solo il codice che ha instrumentato. IntelliTest non è in grado di instrumentare determinate parti di **mscorlib**, tra cui la libreria Reflection. **DynamicMethod** non può essere instrumentato.

Come soluzione alternativa è consigliabile configurare una modalità di test in cui tali metodi risiedono in tipi in un assembly dinamico. Tuttavia, anche se alcuni metodi non sono instrumentati, IntelliTest prova a esaminare la massima quantità possibile di codice instrumentato.

### <a name="platform"></a>Piattaforma

IntelliTest è supportato solo su .NETFramework X86 a 32 bit.

### <a name="language"></a>Linguaggio

In linea di principio IntelliTest può analizzare programmi .NET arbitrari, scritti in qualsiasi linguaggio .NET. Tuttavia in Visual Studio IntelliTest supporta solo C#.

### <a name="symbolic-reasoning"></a>Ragionamento simbolico

IntelliTest usa un [risolutore di vincoli](input-generation.md#constraint-solver) automatico per determinare quali valori sono rilevanti per il test e il programma sottoposto a test. Tuttavia le capacità del risolutore di vincoli sono e saranno sempre limitate.

### <a name="incorrect-stack-traces"></a>Analisi dello stack non corrette

Dato che IntelliTest rileva e "rigenera" eccezioni in ogni metodo instrumentato, i numeri di riga nelle analisi dello stack non saranno corretti. Questa è una limitazione intrinseca dell'istruzione "rethrow".

## <a name="further-reading"></a>Ulteriori informazioni

* [Post di blog introduttivo](https://blogs.msdn.microsoft.com/visualstudioalm/2014/11/19/introducing-smart-unit-tests/) su MSDN.
* [Generare unit test per il codice con IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
