---
title: "CA1036: Eseguire l'override di metodi su tipi confrontabili"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12254202e2bae5a0846d2772006514eb470b5bdf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Eseguire l'override di metodi su tipi confrontabili
|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto implementa il <xref:System.IComparable?displayProperty=fullName> l'interfaccia e non esegue l'override <xref:System.Object.Equals%2A?displayProperty=fullName> o non overload dell'operatore specifico del linguaggio per uguaglianza, ineguaglianza, minore di o maggiore di. La regola non segnala una violazione se il tipo eredita solo un'implementazione dell'interfaccia.

## <a name="rule-description"></a>Descrizione della regola
 I tipi che definiscono un ordinamento personalizzato implementano la <xref:System.IComparable> interfaccia. Il <xref:System.IComparable.CompareTo%2A> metodo restituisce un valore intero che indica l'ordinamento corretto per le due istanze del tipo. Questa regola identifica i tipi di impostare un ordine decrescente. Ciò implica che il significato ordinario di uguaglianza, ineguaglianza, minore di, maggiore di e non si applicano. Quando si fornisce un'implementazione di <xref:System.IComparable>, è necessario eseguire anche l'override <xref:System.Object.Equals%2A> in modo che restituisca valori coerenti con <xref:System.IComparable.CompareTo%2A>. Se esegue l'override <xref:System.Object.Equals%2A> e creazione di codice in un linguaggio che supporta l'overload degli operatori, è necessario fornire anche operatori coerenti con <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, eseguire l'override <xref:System.Object.Equals%2A>. Se il linguaggio di programmazione supporta l'overload degli operatori, specificare gli operatori seguenti:

-   op_Equality

-   op_Inequality

-   op_LessThan

-   op_GreaterThan

 In c#, i token vengono utilizzati per rappresentare questi operatori sono i seguenti: = =,! =, \<, e >.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se la violazione è causata da operatori mancanti e il linguaggio di programmazione non supporta l'overload degli operatori, come accade con Visual Basic. È inoltre possibile eliminare un avviso per da questa regola quando viene generato per gli operatori di uguaglianza diverso op_Equality se si determina che implementa gli operatori non ha senso nel contesto di applicazione. Tuttavia, deve sempre essere op_Equality e l'operatore = =, se si esegue l'override di Object. Equals.

## <a name="example"></a>Esempio
 Nell'esempio seguente contiene un tipo che implementa correttamente <xref:System.IComparable>. Commenti del codice identificano i metodi che soddisfano varie regole correlate a <xref:System.Object.Equals%2A> e <xref:System.IComparable> interfaccia.

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>Esempio
 La seguente applicazione controlla il comportamento del <xref:System.IComparable> implementazione illustrata in precedenza.

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Vedere anche
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName> [Operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators)