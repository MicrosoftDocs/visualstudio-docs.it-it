---
title: 'CA2218: Sostituzione GetHashCode all''override di Equals | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eed9ae032a89eb30785acb71feac47d6c4f8cdc3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: Eseguire l'override di GetHashCode all'override di Equals
|||  
|-|-|  
|TypeName|OverrideGetHashCodeOnOverridingEquals|  
|CheckId|CA2218|  
|Category|Microsoft. Usage|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Esegue l'override di un tipo pubblico <xref:System.Object.Equals%2A?displayProperty=fullName> ma non esegue l'override <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descrizione della regola  
 <xref:System.Object.GetHashCode%2A>Restituisce un valore, in base all'istanza corrente, adatto per algoritmi di hash e strutture di dati, ad esempio una tabella hash. Due oggetti sono dello stesso tipo e uguali devono restituire lo stesso codice hash per garantire il corretto funzionano delle istanze dei tipi seguenti:  
  
-   <xref:System.Collections.Hashtable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   Tipi che implementano<xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, fornire un'implementazione di <xref:System.Object.GetHashCode%2A>. Per una coppia di oggetti dello stesso tipo, è necessario assicurarsi che l'implementazione restituisce lo stesso valore se l'implementazione di <xref:System.Object.Equals%2A> restituisce `true` per la coppia.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="class-example"></a>Esempio di classe  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente viene illustrata una classe (tipo di riferimento) che violano questa regola.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### <a name="comments"></a>Commenti  
 Nell'esempio seguente consente di correggere la violazione eseguendo l'override <xref:System.Object.GetHashCode>.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
## <a name="structure-example"></a>Esempio di struttura  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente viene illustrata una struttura (tipo di valore) che violano questa regola.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
### <a name="comments"></a>Commenti  
 Nell'esempio seguente consente di correggere la violazione eseguendo l'override <xref:System.Object.GetHashCode>.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.Hashtable?displayProperty=fullName>   
 [Operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators)