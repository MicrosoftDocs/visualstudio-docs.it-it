---
title: 'CA1823: Evitare campi privati non utilizzati'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b8d3e1738b217d836bd0e4ca60178d2d65ac686
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitare campi privati non utilizzati
|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Questa regola viene segnalata quando un campo privato nel codice esiste ma non viene utilizzato da qualsiasi percorso di codice.

## <a name="rule-description"></a>Descrizione della regola
 Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il campo o aggiungere codice che lo utilizza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Rivedere i parametri non usati](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)