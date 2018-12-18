---
title: 'Ca1003: Utilizzare istanze di gestori eventi generici'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 32eb25cb6bc3fc998f57a6ca6e4dad2e088f25ad
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1003-use-generic-event-handler-instances"></a>Ca1003: Utilizzare istanze di gestori eventi generici
|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo contiene un delegato che restituisce void, la cui firma contiene due parametri (il primo è un oggetto e il secondo è un tipo assegnabile a EventArgs) la destinazione dell'assembly contenente [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Descrizione della regola
 Prima di [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]per passare informazioni personalizzate al gestore dell'evento, un nuovo delegato che era necessario dichiarare che specifica una classe derivata dalla <xref:System.EventArgs?displayProperty=fullName> classe. Non è più true in [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], quali introdotto il <xref:System.EventHandler%601?displayProperty=fullName> delegato. Questo delegato generico consente a qualsiasi classe che deriva da <xref:System.EventArgs> da utilizzare con il gestore dell'evento.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il delegato e sostituire il relativo utilizzo, utilizzando il <xref:System.EventHandler%601?displayProperty=fullName> delegato. Se il delegato viene generato automaticamente dal [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilatore, modificare la sintassi della dichiarazione di evento da utilizzare il <xref:System.EventHandler%601?displayProperty=fullName> delegato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un delegato che viola la regola. Nel [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] esempio commenti descrivono come modificare l'esempio per soddisfare la regola. Ad esempio c# segue un esempio che illustra il codice modificato.

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene rimossa la dichiarazione di delegato dall'esempio precedente, che soddisfa la regola e sostituisce l'uso nel `ClassThatRaisesEvent` e `ClassThatHandlesEvent` metodi usando il <xref:System.EventHandler%601?displayProperty=fullName> delegato.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Usare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
 [Generics](/dotnet/csharp/programming-guide/generics/index)