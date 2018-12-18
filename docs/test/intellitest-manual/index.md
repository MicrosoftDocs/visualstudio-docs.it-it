---
title: Manuale di riferimento per IntelliTest | Strumenti di test per Microsoft Developer | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest Reference Manual, IntelliTest
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 30c23fc51f136d7fc3dcfeca191f5c469fb1e331
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="intellitest-reference-manual"></a>Manuale di riferimento per IntelliTest

## <a name="contents"></a>Sommario

* **[Panoramica di IntelliTest](introduction.md)**
  - [Hello World di IntelliTest](introduction.md#hello-world)
  - [Limitazioni](introduction.md#limitations)
    * [Non determinismo](introduction.md#nondeterminism)
    * [Concorrenza](introduction.md#concurrency)
    * [Codice nativo](introduction.md#native-code)
    * [Piattaforma](introduction.md#platform)
    * [Lingua](introduction.md#language)
    * [Ragionamento simbolico](introduction.md#symbolic-reasoning)
    * [Analisi dello stack non corrette](introduction.md#incorrect-stack)
  - [Altre informazioni](introduction.md#further-reading)<p>&nbsp;</p>

* **[Introduzione a IntelliTest](getting-started.md)**
  - [Attributi importanti](getting-started.md#important-attributes)
  - [Classi helper statiche importanti](getting-started.md#helper-classes)<p>&nbsp;</p>
 
* **[Generazione di test](test-generation.md)**
  - [Generatori di test](test-generation.md#test-generators)
  - [Unit test con parametri](test-generation.md#parameterized-unit-testing)
  - [Unit test generici con parametri](test-generation.md#generic-parameterized)
  - [Autorizzazione delle eccezioni](test-generation.md#allowing-exceptions)
  - [Test dei tipi interni](test-generation.md#internal-types)
  - [Presupposti e asserzioni](test-generation.md#assumptions-and-assertions)
  - [Precondizione](test-generation.md#precondition)
  - [Postcondizione](test-generation.md#postcondition)
  - [Errori di test](test-generation.md#test-failures)
  - [Configurazione e deconfigurazione](test-generation.md#setup-teardown)
  - [Altre informazioni](test-generation.md#further-reading)<p>&nbsp;</p>

* **[Generazione di input](input-generation.md)**
  - [Risolutore di vincoli](input-generation.md#constraint-solver)
  - [Code coverage dinamico](input-generation.md#dynamic-code-coverage)
  - [Integer e float](input-generation.md#integers-and-floats)
  - [Oggetti](input-generation.md#objects)
  - [Creazione di istanze di classi esistenti](input-generation.md#existing-classes)
  - [Visibilità](input-generation.md#visibility)
  - [Simulazioni con parametri](input-generation.md#parameterized-mocks)
  - [Struct](input-generation.md#structs)
  - [Matrici e stringhe](input-generation.md#arrays-and-strings)
  - [Recupero di input aggiuntivi](input-generation.md#additional-inputs)
  - [Altre informazioni](input-generation.md#further-reading)<p>&nbsp;</p>

* **[Limiti di esplorazione](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)<p>&nbsp;</p>

* **[Glossario degli attributi](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)<p>&nbsp;</p>

* **[Impostazioni a cascata](settings-waterfall.md)**

* **[Classi helper statiche](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)<p>&nbsp;</p>

* **[Avvisi ed errori](warnings-and-errors.md)**
  - [MaxBranches superato](warnings-and-errors.md#maxbranches-exceeded)
  - [MaxConstraintSolverTime superato](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [MaxConditions superato](warnings-and-errors.md#maxconditions-exceeded)
  - [MaxCalls superato](warnings-and-errors.md#maxcalls-exceeded)
  - [MaxStack superato](warnings-and-errors.md#maxstack-exceeded)
  - [MaxRuns superato](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests superato](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Non è possibile concretizzare la soluzione](warnings-and-errors.md#cannot-concretize-solution)
  - [Serve aiuto per costruire l'oggetto](warnings-and-errors.md#help-construct)
  - [Serve aiuto per trovare i tipi](warnings-and-errors.md#help-types)
  - [Tipo utilizzabile ipotizzato](warnings-and-errors.md#usable-type-guessed)
  - [Errore imprevisto nell'esplorazione](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Chiamata di metodo non instrumentato](warnings-and-errors.md#uninstrumented-method-called)
  - [Chiamata di metodo esterno](warnings-and-errors.md#external-method-called)
  - [Chiamata di metodo non instrumentabile](warnings-and-errors.md#uninstrumentable-method-called)
  - [Problema di testabilità](warnings-and-errors.md#testability-issue)
  - [Limitazione](warnings-and-errors.md#limitation)
  - [Rilevata mancata corrispondenza della chiamata](warnings-and-errors.md#observed-call-mismatch)
  - [Valore memorizzato in un campo statico](warnings-and-errors.md#value-static-field)<p>&nbsp;</p>

## <a name="got-feedback"></a>Commenti?

Pubblicare idee e richieste di funzionalità in **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
