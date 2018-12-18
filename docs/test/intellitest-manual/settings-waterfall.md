---
title: Impostazioni a cascata | Strumento di test per sviluppatori Microsoft IntelliTest | Microsoft Docs
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9265fd0ada4f966f5d5fba01591e10f5f0a4194f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="settings-waterfall"></a>Impostazioni a cascata

Il concetto di impostazioni a cascata significa che l'utente può specificare impostazioni a livello di **assembly**, **fixture** ed **esplorazione**: 

* Assembly: [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Fixture: [PexClass](attribute-glossary.md#pexclass)
* Esplorazione: [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Le impostazioni specificate a livello di **assembly** hanno effetto su tutte le fixture e le esplorazioni sotto tale assembly. Le impostazioni specificate a livello di **fixture** hanno effetto su tutte le esplorazioni sotto tale fixture. Le impostazioni figlio hanno la precedenza: se un'impostazione è definita sia a livello di **assembly** che a livello di **fixture** viene usata l'impostazione definita a livello di **fixture**.

Si noti che alcune impostazioni sono specifiche per il livello di **assembly** o il livello di **fixture**. 

**Esempio**

```
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500 
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>Commenti?

Pubblicare idee e richieste di funzionalità in **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
