---
title: Glossario degli attributi | Strumento di test per sviluppatori Microsoft IntelliTest | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fd799598f7e497c217024965d7a83ff1df322acd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="attribute-glossary"></a>Glossario degli attributi

## <a name="attributes-by-namespace"></a>Attributi per spazio dei nomi

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
     - [PexExplorationAttributeBase](#pexexplorationattributebase)<p />

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)<p />

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)<p />

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)<p />

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Questo attributo consente di asserire che il valore governato non può essere **null**. Può essere allegato a:

* un **parametro** di un metodo di test con parametri

  ```
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* un **campo**

  ```
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* un **tipo**

  ```
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Può anche essere allegato a un assembly, una fixture o un metodo di test. In questo caso i primi argomenti devono indicare a quale campo o tipo sono applicati i presupposti. Quando l'attributo è applicato a un tipo, viene applicato a tutti i campi con questo tipo formale.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Attributo che contrassegna una classe contenente *explorations*. Equivale all'attributo **TestClassAttribute** di MSTest (**TestFixtureAttribute** in NUnit). L'attributo è facoltativo.

Le classi contrassegnate con [PexClass](#pexclass) devono *poter essere costruite per impostazione predefinita*:

* tipo esportato pubblicamente
* costruttore predefinito
* non astratta

Se la classe non soddisfa tali requisiti, viene restituito un errore e l'esplorazione non riesce.

È anche consigliabile rendere le classi **parziali** in modo che IntelliTest sia in grado di generare nuovi test che fanno parte della classe, ma in un file separato. Questo approccio risolve molti problemi dovuti alla [visibilità](input-generation.md#visibility) ed è una tecnica tipica in C#.

**Suite e categorie aggiuntive**:

```
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Indicazione del tipo sottoposto a test**:

```
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

La classe può contenere i metodi annotati con [PexMethod](#pexmethod). IntelliTest riconosce inoltre i [metodi di configurazione e deconfigurazione](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Questo attributo consente di usare una tupla del tipo per creare un'istanza di uno [unit test con parametri generico](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Attributo che identifica un metodo come [unit test con parametri](test-generation.md#parameterized-unit-testing).
Il metodo deve trovarsi all'interno di una classe contrassegnata con l'attributo [PexClass](#pexclass).

IntelliTest genera test tradizionali e senza parametri, che chiamano lo [unit test con parametri](test-generation.md#parameterized-unit-testing) con parametri diversi.

Lo unit test con parametri:

* deve essere un metodo di istanza
* deve essere [visibile](input-generation.md#visibility) alla classe di test in cui vengono inseriti i test generati in base alle [impostazioni a cascata](settings-waterfall.md)
* può accettare qualsiasi numero di parametri
* può essere generico

**Esempio**

```
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Altre informazioni](https://msdn.microsoft.com/library/microsoft.pex.framework.pexexplorationattributebase.aspx)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Questo attributo può essere impostato a livello di assembly per eseguire l'override di valori predefiniti delle impostazioni per tutte le esplorazioni.

```
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "Naked")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Questo attributo specifica un assembly attualmente testato dal progetto di test corrente. 

```
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Attributo usato per specificare un assembly da instrumentare.

**Esempio**

```
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Questo attributo indica a IntelliTest che può usare un tipo particolare per creare un'istanza di interfacce o tipi di base (astratti).

**Esempio**

```
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Se questo attributo è associato a [PexMethod](#pexmethod) o a [PexClass](#pexclass), modifica la logica di IntelliTest predefinita che indica se il test ha esito negativo. Il test non verrà considerato come non riuscito, anche se viene generata l'eccezione specificata.

**Esempio**

Il test seguente specifica che il costruttore di **Stack** può generare un'eccezione **ArgumentOutOfRangeException**:

```
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

Il filtro è allegato a una fixture come indicato di seguito (può anche essere definito a livello di assembly o test):

```
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Altre informazioni](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromassemblyattribute.aspx)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Altre informazioni](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeattribute.aspx)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Altre informazioni](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeundertestattribute.aspx)

## <a name="got-feedback"></a>Commenti?

Pubblicare idee e richieste di funzionalità in **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
