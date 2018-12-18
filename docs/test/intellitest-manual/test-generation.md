---
title: Generazione di test | Strumento di test per sviluppatori Microsoft IntelliTest | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 259ff0818cebde6d7c603428c6cdb88cd51ca293
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="test-generation"></a>Generazione di test

Nel testing unità tradizionale la composizione di un test richiede diversi ingredienti:

```
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

Il test è costituito da diversi aspetti:

* Corregge una [sequenza di chiamate al metodo](test-generation.md#test-generators)
* Corregge gli argomenti con cui vengono chiamati i metodi e gli argomenti sono gli [input del test](input-generation.md)
* Convalida il comportamento previsto dell'applicazione testata indicando un set di [asserzioni](#assumptions-and-assertions)

IntelliTest spesso è in grado di determinare automaticamente i valori degli argomenti rilevanti per gli [unit test con parametri](#parameterized-unit-testing), che specificano la sequenza di chiamate al metodo e asserzioni.

<a name="test-generators"></a>
## <a name="test-generators"></a>Generatori di test

IntelliTest genera i test case selezionando una sequenza di metodi dell'implementazione testata da eseguire e quindi generando input per i metodi durante il controllo delle asserzioni per i dati derivati.

Un [unit test con parametri](#parameterized-unit-testing) specifica direttamente una sequenza di chiamate al metodo nel proprio corpo.

Quando è necessario costruire oggetti, IntelliTest esegue una chiamata ai costruttori e i metodi factory vengono aggiunti automaticamente alla sequenza come richiesto.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Unit test con parametri

Gli *unit test con parametri* sono test che accettano parametri. A differenza degli unit test tradizionali, che in genere sono metodi chiusi, gli unit test con parametri accettano qualsiasi set di parametri. Tutto qui? Sì, da qui IntelliTest tenterà di [generare il set (minimo) di input](input-generation.md) che [copre completamente](input-generation.md#dynamic-code-coverage) il codice raggiungibile dal test.

Gli unit test con parametri vengono definiti usando l'attributo personalizzato [PexMethod](attribute-glossary.md#pexmethod) in modo simile a MSTest (o NUnit, xUnit). Sono metodi di istanza raggruppati logicamente in classi contrassegnate con [PexClass](attribute-glossary.md#pexclass). L'esempio seguente illustra un unit test con parametri semplice archiviato nella classe **MyPexTest**:

```
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

dove **ReplaceFirstChar** è un metodo che sostituisce il primo carattere di una stringa:

```
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Da questo test IntelliTest può automaticamente [generare gli input](input-generation.md) per un unit test con parametri che copre tutti i percorsi di esecuzione del codice testato. Ogni input che riguarda un percorso di esecuzione diverso viene "serializzato" come unit test:

```
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>Unit test generici con parametri

Gli unit test con parametri possono essere metodi generici. In questo caso l'utente deve specificare i tipi usati per creare un'istanza del metodo con [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

```
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>Autorizzazione delle eccezioni

IntelliTest offre numerosi attributi di convalida per consentire la valutazione delle eccezioni dividendo le eccezioni previste dalle eccezione impreviste.

Le eccezioni previste generano test case negativi con l'annotazione appropriata, ad esempio **ExpectedException(typeof(*xxx*))**, mentre le eccezioni impreviste generano test case non superati.

```
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

I validator sono:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): consente un tipo particolare di eccezione da qualsiasi posizione
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): consente un tipo particolare di eccezione da un assembly specificato
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): consente un tipo particolare di eccezione da un tipo specificato
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): consente un tipo particolare di eccezione dal tipo sottoposto a test

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Test dei tipi interni

IntelliTest è in grado di testare i tipi interni, purché siano visibili. Affinché IntelliTest veda i tipi, le procedure guidate di Visual Studio IntelliTest aggiungono al progetto di prodotto o di test l'attributo seguente:

```
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Presupposti e asserzioni

Gli utenti possono usare presupposti e asserzioni per esprimere [precondizioni](#precondition) (presupposti) e [postcondizioni](#postcondition) (asserzioni) relative ai test. Quando IntelliTest genera un set di valori di parametro ed "esplora" il codice, potrebbe violare un presupposto del test. In questo caso non verrà generato un test per quel percorso, che verrà automaticamente ignorato.

Le asserzioni sono un concetto noto nei framework dei normali unit test, quindi IntelliTest "riconosce" già le classi **Assert** predefinite disponibili in ogni framework di test supportato. Tuttavia, nella maggior parte dei framework non è presente una classe **Assume**. In questo caso IntelliTest specifica una classe [PexAssume](static-helper-classes.md#pexassume). Se non si vuole usare un framework di test esistente, IntelliTest offre anche una classe [PexAssert](static-helper-classes.md#pexassert).

```
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

In particolare, il presupposto di non invalidità può essere codificato come attributo personalizzato:

```
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Precondizione

Una precondizione di un metodo esprime le condizioni in cui il metodo avrà esito positivo.

In genere, la precondizione viene applicata controllando i parametri e lo stato dell'oggetto e generando un'accezione **ArgumentException** o **InvalidOperationException** in caso di violazione.

In IntelliTest una precondizione di un [unit test con parametri](#parameterized-unit-testing) viene espressa con [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Postcondizione

Una postcondizione di un metodo esprime le condizioni che devono essere mantenute durante e dopo l'esecuzione del metodo, presupponendo che le relative precondizioni fossero valide.

In genere, la postcondizione viene applicata dalle chiamate ai metodi **Assert**.

In IntelliTest una postcondizione di un [unit test con parametri](#parameterized-unit-testing) viene espressa con [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Errori di test
Quando si considera non superato un test case generato?

1. Se non viene terminato all'interno dei [limiti di percorso configurati](exploration-bounds.md), viene considerato non superato a meno che non sia impostata l'opzione [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)

1. Se il test genera un'eccezione **PexAssumeFailedException**, ha esito positivo. Tuttavia, in genere viene ignorato a meno che l'opzione [TestEmissionFilter](exploration-bounds.md#testemissionfilter) non sia impostata su **Tutti**

1. Se il test viola un'[asserzione](#assumptions-and-assertions), ad esempio generando un'eccezione di violazione dell'asserzione di un framework di unit test, avrà esito negativo

Se nessuna delle situazioni precedenti produce una decisione, un test ha esito positivo esclusivamente se non genera un'eccezione. Le violazioni delle asserzioni vengono trattate esattamente come le eccezioni.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Configurazione e deconfigurazione

Come parte dell'integrazione con i framework di test, IntelliTest supporta il rilevamento e l'esecuzione dei metodi di configurazione e deconfigurazione.

**Esempio**

```
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}

```

<a name="further-reading"></a>
## <a name="further-reading"></a>Ulteriori informazioni

* [Post di blog sull'associazione test-codice](https://blogs.msdn.microsoft.com/visualstudioalm/2015/04/18/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Post di blog su IntelliTest](https://blogs.msdn.microsoft.com/visualstudioalm/2015/07/05/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Commenti?

Pubblicare idee e richieste di funzionalità in **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
