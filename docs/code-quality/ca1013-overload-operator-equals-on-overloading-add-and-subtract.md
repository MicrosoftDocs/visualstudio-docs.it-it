---
title: "CA1013: Eseguire l'overload dell'operatore \"uguale a\" all'overload degli operatori di addizione e sottrazione"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7fd43cc3077c037b70eaa8107563bd8f40b6a096
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione
|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un membro pubblico o protetto implementa gli operatori di addizione o sottrazione senza implementare l'operatore di uguaglianza.

## <a name="rule-description"></a>Descrizione della regola
 Quando le istanze di un tipo possono essere combinate tramite operazioni quali l'addizione e sottrazione, è quasi sempre necessario definire l'uguaglianza per restituire `true` per due istanze che contengono gli stessi valori che costituiscono.

 È possibile utilizzare l'operatore di uguaglianza predefinito in un'implementazione di overload dell'operatore di uguaglianza. Questa operazione causerebbe un overflow dello stack. Per implementare l'operatore di uguaglianza, utilizzare il metodo Equals nell'implementazione. Vedere l'esempio seguente.

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare l'operatore di uguaglianza, in modo che sia matematicamente coerenza con gli operatori di addizione e sottrazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando l'implementazione predefinita dell'operatore di uguaglianza fornisce il comportamento corretto per il tipo.

## <a name="example"></a>Esempio
 L'esempio seguente definisce un tipo (`BadAddableType`) che violano questa regola. Questo tipo deve implementare l'operatore di uguaglianza affinché due istanze in cui gli stessi valori di campo test `true` per verificarne l'uguaglianza. Il tipo `GoodAddableType` viene illustrata l'implementazione corretta. Si noti che questo tipo implementa l'operatore di disuguaglianza anche ed esegue l'override <xref:System.Object.Equals%2A> per soddisfare le altre regole. Un'implementazione completa è necessario implementare anche <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Esempio
 Nell'esempio seguente verifica l'uguaglianza con istanze dei tipi definiti in precedenza in questo argomento per illustrare il comportamento predefinito e il comportamento corretto per l'operatore di uguaglianza.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

 Questo esempio produce il seguente output:

 **Tipo non valido: {2,2} {2,2} sono uguali. Non**
**tipo buona: {3,3} {3,3} sono uguali. Sì**
**tipo buona: {3,3} {3,3} sono = =?   Sì**
**tipo non valido: {2,2} {9,9} sono uguali. Non**
**tipo buona: {3,3} {9,9} sono = =?   No**
## <a name="see-also"></a>Vedere anche
 [Operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators)