---
title: 'CA1000: Non dichiarare membri statici su tipi generici | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 11bef403ffedee1a22ba615ee1744a7e93f8c1b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: Non dichiarare membri statici su tipi generici
|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo generico visibile esternamente contiene un `static` (`Shared` in Visual Basic) membri.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quando un `static` membro di un tipo generico viene chiamato, l'argomento di tipo deve essere specificato per il tipo. Quando viene chiamato un membro di istanza generica che non supporta l'inferenza, è necessario specificare l'argomento tipo relativo al membro. La sintassi per specificare l'argomento di tipo in questi due casi è diversa e può generare confusione, come illustrato di seguito viene chiamato:  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```csharp  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 In genere, entrambe le dichiarazioni precedenti devono essere evitati in modo che l'argomento di tipo non deve essere specificato quando viene chiamato il membro. Ciò comporta una sintassi per chiamare i membri di generics che non è diversa dalla sintassi per non generics. Per ulteriori informazioni, vedere [CA1004 i: i metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il membro statico o impostarlo su un membro di istanza.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola. Fornisce una sintassi che è facile da comprendere e utilizzare generics riduce il tempo necessario all'apprendimento e aumenta la frequenza di adozione di nuove librerie.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Usare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Generics](/dotnet/csharp/programming-guide/generics/index)