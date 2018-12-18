---
title: "CA2224: Eseguire l'override di Equals all'override dell'operatore"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3640bf69efa20be5c9888118120c337cbd2c105
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Eseguire l'override di Equals all'override dell'operatore
|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo pubblico implementa l'operatore di uguaglianza, ma non esegue l'override <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 L'operatore di uguaglianza deve essere un modo pratico sintatticamente per accedere alle funzionalità del <xref:System.Object.Equals%2A> metodo. Se si implementa l'operatore di uguaglianza, la logica deve essere identica a quello di <xref:System.Object.Equals%2A>.

 Il compilatore c# genera un avviso se il codice viola questa regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, è necessario rimuovere l'implementazione dell'operatore di uguaglianza oppure eseguire l'override <xref:System.Object.Equals%2A> e dispone di due metodi restituiscano gli stessi valori. Se l'operatore di uguaglianza non introduce un comportamento incoerente, è possibile correggere la violazione fornendo un'implementazione di <xref:System.Object.Equals%2A> che chiama il <xref:System.Object.Equals%2A> metodo nella classe base.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È consigliabile escludere un avviso da questa regola se l'operatore di uguaglianza restituisce lo stesso valore l'implementazione ereditata di <xref:System.Object.Equals%2A>. La sezione di esempio include un tipo che è possibile escludere in modo sicuro un avviso da questa regola.

## <a name="examples-of-inconsistent-equality-definitions"></a>Esempi di definizioni di uguaglianza incoerenti

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrato un tipo con definizioni incoerenti di uguaglianza. `BadPoint` la modifica del significato di uguaglianza, fornendo un'implementazione personalizzata dell'operatore di uguaglianza, ma non esegue l'override <xref:System.Object.Equals%2A> in modo che si comporta in modo identico.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

## <a name="example"></a>Esempio
 Il codice seguente viene verificato il comportamento di `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

 Questo esempio produce il seguente output:

 **a = (1,1 [0]) e b = (2,2 [1]) sono uguali. Non**
**un = = b? Non**
**a1 e un oggetto sono uguali. Sì**
**a1 = = un? Sì**
**bcopy e b sono uguali. Non**
**b = = bcopy? Sì**
## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che tecnicamente viola questa regola, ma non si comportano in modo incoerente.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

## <a name="example"></a>Esempio
 Il codice seguente viene verificato il comportamento di `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

 Questo esempio produce il seguente output:

 **a (1,1) = a e b = (2,2) sono uguali. Non**
**un = = b? Non**
**a1 e un oggetto sono uguali. Sì**
**a1 = = un? Sì**
**bcopy e b sono uguali. Sì**
**b = = bcopy? Sì**
## <a name="class-example"></a>Esempio di classe

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrata una classe (tipo di riferimento) che violano questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

## <a name="example"></a>Esempio
 Nell'esempio seguente consente di correggere la violazione eseguendo l'override <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Esempio di struttura

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrata una struttura (tipo di valore) che violano questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

## <a name="example"></a>Esempio
 Nell'esempio seguente consente di correggere la violazione eseguendo l'override <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)