---
title: 'CA1707: Gli identificatori non devono contenere caratteri di sottolineatura'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4eed69f8c08d6106bf30e9c1884512e384a7a269
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Gli identificatori non devono contenere caratteri di sottolineatura
|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Category|Microsoft.Naming|
|Modifica importante|Sostanziale - Quando generato su assembly<br /><br /> Non sostanziale - Quando generato su parametri di tipo|

## <a name="cause"></a>Causa
 Il nome di un identificatore contiene il carattere di sottolineatura (_).

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione i nomi degli identificatori non contengono il carattere di sottolineatura (_). La regola controlla gli spazi dei nomi, tipi, membri e parametri.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere tutti i caratteri di sottolineatura dal nome.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)