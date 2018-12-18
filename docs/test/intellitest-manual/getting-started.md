---
title: Creare stub di metodo di unit test con il comando Crea unit test | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Get started
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 9016006f9774c4a9eff2937f32543b9f8d9f5fb8
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
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
