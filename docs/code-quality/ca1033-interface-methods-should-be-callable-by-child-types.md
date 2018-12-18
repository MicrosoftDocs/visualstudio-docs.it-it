---
title: 'CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c41b19d9d4a82e25223a9cf7b04034b37c3f45fb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio
|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente non sealed fornisce un'implementazione di metodo esplicita di un'interfaccia pubblica e non fornisce un metodo visibile esternamente alternativo con lo stesso nome.

## <a name="rule-description"></a>Descrizione della regola
 Si consideri un tipo di base che implementa in modo esplicito un metodo di interfaccia pubblica. Un tipo che deriva dal tipo di base può accedere al metodo di interfaccia ereditati solo tramite un riferimento all'istanza corrente (`this` in c#) che viene eseguito il cast all'interfaccia. Se il tipo derivato (in modo esplicito) implementa nuovamente il metodo di interfaccia ereditati, l'implementazione di base non sono più accessibili. La chiamata tramite il riferimento all'istanza corrente richiamerà l'implementazione di derivata. In questo modo la ricorsione e un potenziale overflow dello stack.

 Questa regola segnala una violazione per un'implementazione esplicita di <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> quando visibile esternamente `Close()` o `System.IDisposable.Dispose(Boolean)` metodo è fornito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare un nuovo metodo che espone la stessa funzionalità ed è visibile ai tipi derivati oppure passare a un'implementazione non esplicita. Se una modifica sostanziale è accettabile, alternativa, è possibile rendere il tipo sealed.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se viene fornito con la stessa funzionalità, ma un nome diverso rispetto al metodo implementato in modo esplicito un metodo visibile esternamente.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `ViolatingBase`, che viola la regola e un tipo, `FixedBase`, che mostra una correzione per la violazione.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Vedere anche
 [Interfacce](/dotnet/csharp/programming-guide/interfaces/index)