---
title: 'CA1038: Gli enumeratori devono essere fortemente tipizzati | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 84ddea0bebd5c3811da84abadd207b839ec8be48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Gli enumeratori devono essere fortemente tipizzati
|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo pubblico o protetto implementa <xref:System.Collections.IEnumerator?displayProperty=fullName> ma non fornisce una versione fortemente tipizzata di <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> proprietà. Tipi derivati dai seguenti tipi sono interessati da questa regola:  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## <a name="rule-description"></a>Descrizione della regola  
 La regola richiede <xref:System.Collections.IEnumerator> le implementazioni forniscano anche una versione fortemente tipizzata del <xref:System.Collections.IEnumerator.Current%2A> proprietà in modo che gli utenti non devono eseguire il cast il valore restituito al tipo sicuro quando utilizzano la funzionalità fornita dall'interfaccia. Questa regola presuppone che il tipo che implementa <xref:System.Collections.IEnumerator> contiene una raccolta di istanze di un tipo più sicuro <xref:System.Object>.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare in modo esplicito la proprietà dell'interfaccia (dichiararla come `IEnumerator.Current`). Aggiungere una versione fortemente tipizzata pubblica della proprietà, dichiarata come `Current`, e che restituisce un oggetto fortemente tipizzato.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola quando si implementa un enumeratore basato su oggetti per l'utilizzo con una raccolta basata su oggetti, ad esempio un albero binario. I tipi che estendono la nuova raccolta verranno definire l'enumeratore fortemente tipizzato ed espongono la proprietà fortemente tipizzata.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il modo corretto per implementare una classe fortemente tipizzata <xref:System.Collections.IEnumerator> tipo.  
  
 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>