---
title: 'CA2204: I valori letterali devono essere digitati in modo corretto'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81989ebce0319669a03d62a504f87a0500400cd9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: I valori letterali devono essere digitati in modo corretto

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Una valore letterale stringa viene passata come argomento per un parametro localizzabile, o a una proprietà localizzabile, e la stringa contiene uno o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.

## <a name="rule-description"></a>Descrizione della regola

Questa regola consente di controllare una stringa letterale che viene passata come un valore per un parametro o una proprietà quando uno o più delle seguenti condizioni sono true:

- Il <xref:System.ComponentModel.LocalizableAttribute> attributo di parametro o la proprietà è impostata su true.

- Il nome di parametro o la proprietà contiene "Text", "Messaggio" o "Didascalia".

- Il nome della variabile di stringa che viene passato a un <xref:System.Console.Write%2A> o <xref:System.Console.WriteLine> è "value" o "format".

Questa regola analizza la stringa letterale in parole, suddivisione in token le parole composte e controlla l'ortografia di ogni parola o token. Per informazioni sull'algoritmo di analisi, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Linguaggio

Il correttore ortografico attualmente controlla solo a dizionari le impostazioni cultura basate su inglese. È possibile modificare le impostazioni cultura del progetto nel file di progetto, aggiungendo il **CodeAnalysisCulture** elemento.

Ad esempio:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Se si imposta le impostazioni cultura su un valore diverso da delle impostazioni cultura basate su inglese, questa regola di analisi codice invisibile all'utente è disabilitata.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, correggere l'ortografia della parola o aggiungere la parola al dizionario personalizzato. Per informazioni sull'utilizzo di dizionari personalizzati, vedere [procedura: personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi

Non escludere un avviso da questa regola. Correttamente ortografia consente di ridurre la curva di apprendimento necessaria per le nuove librerie software.

## <a name="related-rules"></a>Regole correlate

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)