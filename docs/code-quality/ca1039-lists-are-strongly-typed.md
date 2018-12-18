---
title: 'CA1039: Gli elenchi sono fortemente tipizzati'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4dc14aca81f20a33bce5be99a2ccaf5ccad7d5b0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Gli elenchi sono fortemente tipizzati
|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il tipo pubblico o protetto, il tipo implementa <xref:System.Collections.IList?displayProperty=fullName> ma non fornisce un metodo fortemente tipizzato per uno o più delle operazioni seguenti:

-   IList.Item

-   IList

-   IList.Contains

-   IList.IndexOf

-   IList. Insert

-   IList.Remove

## <a name="rule-description"></a>Descrizione della regola
 La regola richiede <xref:System.Collections.IList> le implementazioni per fornire fortemente membri tipizzati in modo che gli utenti non devono eseguire il cast di argomenti per il <xref:System.Object?displayProperty=fullName> digitare quando utilizzano la funzionalità fornita dall'interfaccia. Il <xref:System.Collections.IList> interfaccia viene implementata da raccolte di oggetti che è possibile accedere tramite indice. Questa regola presuppone che il tipo che implementa <xref:System.Collections.IList> esegua questa operazione per gestire una raccolta di istanze di un tipo più sicuro <xref:System.Object>.

 <xref:System.Collections.IList> implementa il <xref:System.Collections.ICollection?displayProperty=fullName> e <xref:System.Collections.IEnumerable?displayProperty=fullName> interfacce. Se si implementa <xref:System.Collections.IList>, è necessario fornire i membri richiesti fortemente tipizzati per <xref:System.Collections.ICollection>. Se gli oggetti nella raccolta estendono <xref:System.ValueType?displayProperty=fullName>, è necessario fornire un membro fortemente tipizzato per <xref:System.Collections.IEnumerable.GetEnumerator%2A> per evitare un calo delle prestazioni causato dalla conversione boxing; non è obbligatorio quando gli oggetti della raccolta sono un tipo di riferimento.

 Per garantire la conformità con questa regola, implementare i membri di interfaccia in modo esplicito utilizzando nomi nel formato InterfaceName, ad esempio <xref:System.Collections.IList.Add%2A>. I membri di interfaccia esplicita utilizzano i tipi di dati che vengono dichiarati dall'interfaccia. Implementare i membri fortemente tipizzati utilizzando il nome di membro di interfaccia, ad esempio `Add`. Dichiarare i membri fortemente tipizzati come pubblici e dichiarare i parametri e restituire valori di tipo sicuro gestito dalla raccolta. I tipi sicuri sostituiscono i tipi più vulnerabili, ad esempio <xref:System.Object> e <xref:System.Array> che vengono dichiarati dall'interfaccia.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare in modo esplicito <xref:System.Collections.IList> membri e fornire alternative fortemente tipizzate per i membri indicati in precedenza. Per il codice che implementa correttamente il <xref:System.Collections.IList> interfaccia e fornisce la membri fortemente tipizzati, vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola quando si implementa una nuova raccolta basata su oggetti, ad esempio un elenco collegato, in cui i tipi che estendono la nuova raccolta determinano il tipo sicuro. Questi tipi devono conformarsi a questa regola ed esporre membri fortemente tipizzati.

## <a name="example"></a>Esempio
 Nell'esempio seguente, il tipo `YourType` estende <xref:System.Collections.CollectionBase?displayProperty=fullName>, come avviene per tutte le raccolte fortemente tipizzate. Si noti che <xref:System.Collections.CollectionBase> fornisce l'implementazione esplicita del <xref:System.Collections.IList> interfaccia. Pertanto, è necessario fornire solo i membri fortemente tipizzati per <xref:System.Collections.IList> e <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Gli enumeratori devono essere fortemente tipizzati](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.IList?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>