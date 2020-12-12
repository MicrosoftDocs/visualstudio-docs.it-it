---
title: Direttive di modello di testo T4
description: Informazioni sulle direttive del modello di test T4 e sul modo in cui forniscono istruzioni al motore di trasformazione del modello di testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ddad0010413ebe8e0a53096bb4d90b52050d26a
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363601"
---
# <a name="t4-text-template-directives"></a>Direttive di modello di testo T4

Le direttive forniscono istruzioni al motore di trasformazione del modello di testo.

La sintassi per le direttive è la seguente:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

Tutti i valori di attributo devono essere racchiusi tra virgolette doppie. Se il valore stesso contiene virgolette, è necessario applicare loro il carattere di escape \.

Le direttive sono in genere i primi elementi di un file modello o di un file incluso. Tali elementi non devono essere inseriti in un blocco di codice `<#...#>`, né dopo un blocco della funzionalità di classe `<#+...#>`.

[Direttiva template T4](../modeling/t4-template-directive.md)

```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

[Direttiva parameter T4](../modeling/t4-parameter-directive.md)

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

[Direttiva output T4](../modeling/t4-output-directive.md)

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

[Direttiva assembly T4](../modeling/t4-assembly-directive.md)

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

[Direttiva import T4](../modeling/t4-import-directive.md)

```
<#@ import namespace="namespace" #>
```

[Direttiva include T4](../modeling/t4-include-directive.md)

```
<#@ include file="filePath" #>
```

[Direttiva T4 CleanUpBehavior](../modeling/t4-cleanupbehavior-directive.md)

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

È inoltre possibile creare direttive personalizzate. Per altre informazioni, vedere [creazione di processori di direttive del modello di testo T4 personalizzato](../modeling/creating-custom-t4-text-template-directive-processors.md). Se si utilizza l'SDK di visualizzazione e modellazione per creare un linguaggio DSL, verrà generato un processore di direttiva come parte di tale linguaggio DSL.
