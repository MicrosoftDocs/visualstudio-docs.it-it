---
title: 'CA1006: Non annidare tipi generici nelle firme dei membri'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 120acca8486d65962a5d8e3cd26a05ae8cc5ac78
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: Non annidare tipi generici nelle firme dei membri
|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un membro visibile esternamente contiene una firma che contiene un argomento tipo annidato.

## <a name="rule-description"></a>Descrizione della regola
 Un argomento di tipo annidato è un argomento di tipo che è anche un tipo generico. Per chiamare un membro la cui firma contiene un argomento tipo annidato, l'utente deve creare un'istanza su un tipo generico e passare il tipo al costruttore di un secondo tipo generico. La sintassi e la procedura necessarie sono complesse ed è opportuno evitarle.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la progettazione per rimuovere l'argomento di tipo annidato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Fornisce una sintassi che è facile da comprendere e utilizzare generics riduce il tempo necessario all'apprendimento e aumenta la frequenza di adozione di nuove librerie.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che viola la regola e la sintassi necessaria per chiamare il metodo.

 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Usare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
 [Generics](/dotnet/csharp/programming-guide/generics/index)