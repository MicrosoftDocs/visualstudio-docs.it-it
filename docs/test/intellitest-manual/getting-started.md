---
title: Creare stub di metodo di unit test con il comando Crea unit test | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b87796cd0534129170931c3a527b38ac176bd300
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="get-started-with-microsoft-intellitest"></a>Introduzione a Microsoft IntelliTest

* Se questa è la prima volta che si usa IntelliTest:
  * guardare il [video di Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * leggere questa [panoramica su MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * leggere la nostra [documentazione](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Porre domande sull'[overflow dello stack](http://stackoverflow.com/questions/tagged/intellitest)
* Leggere il resto del presente manuale di riferimento
* Stampare questa pagina per usarla come riferimento rapido

## <a name="important-attributes"></a>Attributi importanti

* [PexClass](attribute-glossary.md#pexclass) contrassegna un tipo contenente **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) contrassegna un **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) contrassegna un parametro non null

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) associa un progetto di test a un progetto
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) specifica un assembly da instrumentare

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a> Classi helper statiche importanti

* [PexAssume](static-helper-classes.md#pexassume) valuta i presupposti (filtro di input)
* [PexAssert](static-helper-classes.md#pexassert) valuta le asserzioni
* [PexChoose](static-helper-classes.md#pexchoose) genera nuove scelte (input aggiuntivi)
* [PexObserve](static-helper-classes.md#pexobserve) registra i valori in tempo reale nei test generati

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>Commenti?

Pubblicare idee e richieste di funzionalità in [UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest).
