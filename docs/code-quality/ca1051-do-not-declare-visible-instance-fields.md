---
title: 'CA1051: Non dichiarare campi di istanza visibili'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb322ffb6f3603001e9fa673eb9daf9f28d73b18
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Non dichiarare campi di istanza visibili
|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente contiene un campo di istanza visibili esternamente.

## <a name="rule-description"></a>Descrizione della regola
 L'utilizzo principale di un campo deve essere come dettaglio di implementazione. I campi devono essere `private` o `internal` e devono essere esposti tramite proprietà. È facile accedere a una proprietà è di accedere a un campo e il codice nelle funzioni di accesso di una proprietà può essere modificato espandono le funzionalità del tipo senza introdurre modifiche di rilievo. Le proprietà che restituiscono solo il valore di un campo privato o interno sono ottimizzate per l'esecuzione coerente con l'accesso a un campo. miglioramento delle prestazioni molto ridotto è associata con l'utilizzo di campi visibili esternamente rispetto alle proprietà.

 Fa riferimento visibile esternamente a `public`, `protected`, e `protected internal` (`Public`, `Protected`, e `Protected Friend` in Visual Basic) dei livelli di accessibilità.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere il campo `private` o `internal` ed esporlo tramite una proprietà visibile esternamente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Campi visibili esternamente non offre vantaggi che non sono disponibili per le proprietà. Inoltre, i campi pubblici non possono essere protetti da [le richieste di collegamento](/dotnet/framework/misc/link-demands). Vedere [CA2112: i tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo (`BadPublicInstanceFields`) che violano questa regola. `GoodPublicInstanceFields` Mostra il codice corretto.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Vedere anche
 [Richieste di collegamento](/dotnet/framework/misc/link-demands)