---
title: "CA2233: Evitare l'overflow delle operazioni"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a79c69e12aa1b4d8e8c4bd9ff4b637b788b68ee8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Evitare l'overflow delle operazioni
|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo esegue un'operazione aritmetica e non convalida gli operandi in anticipo per evitare l'overflow.

## <a name="rule-description"></a>Descrizione della regola
 Operazioni aritmetiche non devono essere eseguite senza prima convalidare gli operandi per assicurarsi che il risultato dell'operazione non è compreso nell'intervallo di valori possibili per i tipi di dati coinvolti. A seconda del contesto di esecuzione e i tipi di dati coinvolti, overflow aritmetico può generare sia un <xref:System.OverflowException?displayProperty=fullName> o scartati i bit più significativi del risultato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, convalidare gli operandi prima di eseguire l'operazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se i valori possibili di operandi non causerà mai l'overflow dell'operazione aritmetica.

## <a name="example-of-a-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 Un metodo nell'esempio seguente modifica un valore integer che violano questa regola. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] richiede il **rimuovere** opzione sia disabilitato per questa opzione per attivare overflow di integer.

### <a name="code"></a>Codice
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

### <a name="comments"></a>Commenti
 Se il metodo in questo esempio viene passato <xref:System.Int32.MinValue?displayProperty=fullName>, l'operazione si verificherà un underflow. In questo modo il bit più significativo del risultato per essere eliminata. Il codice seguente viene illustrata questa operazione.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 [VB]

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Output

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Risolvere con la convalida dei parametri di Input

### <a name="description"></a>Descrizione
 Nell'esempio seguente consente di correggere la violazione precedente convalidando il valore di input.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Risolvere con un blocco Checked

### <a name="description"></a>Descrizione
 Nell'esempio seguente consente di correggere la violazione precedente eseguendo il wrapping dell'operazione in un blocco checked. Se l'operazione provoca un overflow, una <xref:System.OverflowException?displayProperty=fullName> verrà generata.

 Si noti che i blocchi selezionati non sono supportati in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Attivare Overflow/Underflow aritmetico Checked
 Se si attiva checked overflow/underflow aritmetico in c#, è equivalente a wrapping di ogni operazione di integer in un blocco checked.

 **Per attivare checked overflow/underflow aritmetico nel linguaggio c#**

1.  In **Esplora**, mouse sul progetto e scegliere **proprietà**.

2.  Nella scheda **Compilazione** scegliere **Avanzate**.

3.  Selezionare **Controlla overflow/underflow aritmetico** e fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
 <xref:System.OverflowException?displayProperty=fullName> [Operatori [c#]](/dotnet/csharp/language-reference/operators/index) [Checked e Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)