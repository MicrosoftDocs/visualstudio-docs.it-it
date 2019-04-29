---
title: 'CA2120: Proteggere i costruttori di serializzazione'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15fd1596fdede3d13d603e7df222395a7ef7a277
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545114"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Proteggere i costruttori di serializzazione

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il tipo implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia, non è un delegato o un'interfaccia e viene dichiarata in un assembly che consente ai chiamanti parzialmente attendibili. Il tipo ha un costruttore che accetta un <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> oggetto e un <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> oggetto (la firma del costruttore di serializzazione). Questo costruttore non è protetto da un controllo di sicurezza, ma uno o più costruttori regolari nel tipo viene protetto.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola è rilevante per i tipi che supportano la serializzazione personalizzata. Un tipo supporta la serializzazione personalizzata se implementa il <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia. Il costruttore di serializzazione è obbligatorio e viene utilizzato per deserializzare oppure ricreare gli oggetti che sono stati serializzati utilizzando la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> (metodo). Poiché il costruttore di serializzazione alloca e inizializza gli oggetti, i controlli di sicurezza che sono presenti sui costruttori regolari inoltre devono essere presenti nel costruttore di serializzazione. Se si violano questa regola, i chiamanti che non è stato in caso contrario, creare un'istanza è stato possibile utilizzare il costruttore di serializzazione per eseguire questa operazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, proteggere il costruttore di serializzazione con richieste di sicurezza che sono identici a quelli che proteggono altri costruttori.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non eliminare una violazione della regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>