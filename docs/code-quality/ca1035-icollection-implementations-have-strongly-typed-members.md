---
title: 'CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a3e595046442092c11b068b6df6fde2a9a56e705
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati
|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo pubblico o protetto implementa <xref:System.Collections.ICollection?displayProperty=fullName> ma non fornisce un metodo fortemente tipizzato per <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. La versione fortemente tipizzata di <xref:System.Collections.ICollection.CopyTo%2A> deve accettare due parametri e non può avere un <xref:System.Array?displayProperty=fullName> o una matrice di <xref:System.Object?displayProperty=fullName> come primo parametro.  
  
## <a name="rule-description"></a>Descrizione della regola  
 La regola richiede <xref:System.Collections.ICollection> le implementazioni per fornire fortemente membri tipizzati in modo che gli utenti non devono eseguire il cast di argomenti per il <xref:System.Object> digitare quando utilizzano la funzionalità fornita dall'interfaccia. Questa regola presuppone che il tipo che implementa <xref:System.Collections.ICollection> esegua questa operazione per gestire una raccolta di istanze di un tipo più sicuro <xref:System.Object>.  
  
 L'oggetto <xref:System.Collections.ICollection> implementa l'interfaccia <xref:System.Collections.IEnumerable?displayProperty=fullName>. Se gli oggetti nella raccolta estendono <xref:System.ValueType?displayProperty=fullName>, è necessario fornire un membro fortemente tipizzato per <xref:System.Collections.IEnumerable.GetEnumerator%2A> per evitare un calo delle prestazioni causata dalla conversione boxing. Questo non è obbligatorio quando gli oggetti della raccolta sono un tipo di riferimento.  
  
 Per implementare una versione fortemente tipizzata di un membro di interfaccia, implementare i membri di interfaccia in modo esplicito utilizzando nomi nel formato `InterfaceName.InterfaceMemberName`, ad esempio <xref:System.Collections.ICollection.CopyTo%2A>. I membri di interfaccia esplicita utilizzano i tipi di dati che vengono dichiarati dall'interfaccia. Implementare i membri fortemente tipizzati utilizzando il nome di membro di interfaccia, ad esempio <xref:System.Collections.ICollection.CopyTo%2A>. Dichiarare i membri fortemente tipizzati come pubblici e dichiarare i parametri e restituire valori di tipo sicuro gestito dalla raccolta. I tipi sicuri sostituiscono i tipi più vulnerabili, ad esempio <xref:System.Object> e <xref:System.Array> che vengono dichiarati dall'interfaccia.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare in modo esplicito il membro di interfaccia (dichiararla come <xref:System.Collections.ICollection.CopyTo%2A>). Aggiungere il membro pubblico fortemente tipizzato, dichiarato come `CopyTo`, e fare in modo che accetti una matrice fortemente tipizzata come primo parametro.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola se si implementa una nuova raccolta basata su oggetti, ad esempio un albero binario, in cui i tipi che estendono la nuova raccolta determinano il tipo sicuro. Questi tipi devono conformarsi a questa regola ed esporre membri fortemente tipizzati.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il modo corretto per implementare <xref:System.Collections.ICollection>.  
  
 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1038: Gli enumeratori devono essere fortemente tipizzati](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>