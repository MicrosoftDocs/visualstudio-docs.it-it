---
title: 'CA1823: Evitare campi privati non usati'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47a2ad3b64055584551a63a2333e29286783d8cf
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921353"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitare campi privati non usati

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Category|Microsoft.Performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
Questa regola viene segnalata quando esiste un campo privato nel codice, ma non viene usato da alcun percorso di codice.

## <a name="rule-description"></a>Descrizione della regola
Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rimuovere il campo o aggiungere il codice che lo utilizza.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola in modo sicuro.

## <a name="related-rules"></a>Regole correlate
[CA1812 Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801 Verifica parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Rimuovi variabili locali non usate](../code-quality/ca1804-remove-unused-locals.md)

[CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)