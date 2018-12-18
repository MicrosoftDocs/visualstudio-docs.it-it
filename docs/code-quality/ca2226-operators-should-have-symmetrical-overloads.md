---
title: 'CA2226: Gli operatori devono avere overload simmetrici'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98f5653d326c257e46becd2d7f8ad1091dfcf0c7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Gli operatori devono avere overload simmetrici
|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo implementa l'operatore di uguaglianza o di disuguaglianza e non implementa l'operatore opposto.

## <a name="rule-description"></a>Descrizione della regola
 Non esistono nessun caso in cui è applicabile alle istanze di un tipo di uguaglianza o disuguaglianza e non è definito l'operatore opposto. In genere i tipi di implementano l'operatore di disuguaglianza restituendo il valore negato dell'operatore di uguaglianza.

 Il compilatore c# genera un errore per le violazioni di questa regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare l'uguaglianza e operatori di disuguaglianza o rimuovere quella che è presente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Il tipo non funzionerà in modo che sia coerenza con il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

## <a name="related-rules"></a>Regole correlate
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)