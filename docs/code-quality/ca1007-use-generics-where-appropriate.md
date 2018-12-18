---
title: 'CA1007: Utilizzare generics dove appropriato'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4aa1bb976cdbcc3d3b97e463ce0076bccdd26ba6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Utilizzare generics dove appropriato
|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo visibile esternamente contiene un parametro di riferimento di tipo <xref:System.Object?displayProperty=fullName>la destinazione dell'assembly contenente [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Descrizione della regola
 Un parametro di riferimento è un parametro che viene modificato tramite il `ref` (`ByRef` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) (parola chiave). Il tipo di argomento fornito per un parametro di riferimento deve corrispondere esattamente a un tipo di parametro. Per utilizzare un tipo derivato dal tipo di parametro di riferimento, è necessario innanzitutto eseguire il cast il tipo e assegnato a una variabile del tipo di parametro di riferimento. Utilizzo di un metodo generico consente di tutti i tipi, soggetti a vincoli, deve essere passato al metodo senza prima eseguire il cast di tipo al tipo di parametro di riferimento.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere il metodo generico e sostituire il <xref:System.Object> parametro tramite un parametro di tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente mostra una routine di scambio di utilizzo generico che viene implementata come metodi e non generici. Si noti come in modo efficiente le stringhe vengono scambiate tramite il metodo generico rispetto al metodo non generico.

 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Vedere anche
 [Generics](/dotnet/csharp/programming-guide/generics/index)