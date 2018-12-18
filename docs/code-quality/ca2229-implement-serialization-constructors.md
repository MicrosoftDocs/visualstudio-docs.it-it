---
title: 'CA2229: Implementare costruttori di serializzazione'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d116c77aa01e9b22da3e2037f29deb1b8c47e64c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementare costruttori di serializzazione
|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Il tipo implementa il <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia, non è un delegato o un'interfaccia e una delle seguenti condizioni è vera:

-   Il tipo non dispone di un costruttore che accetta un <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> oggetto e un <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> oggetto (la firma del costruttore di serializzazione).

-   Il tipo è non bloccato e il modificatore di accesso per il costruttore di serializzazione non è protetta (famiglia).

-   Il tipo è sealed e il modificatore di accesso per il costruttore di serializzazione non è privato.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola è rilevante per i tipi che supportano la serializzazione personalizzata. Un tipo supporta la serializzazione personalizzata se implementa il <xref:System.Runtime.Serialization.ISerializable> interfaccia. È necessario il costruttore di serializzazione per deserializzare o ricreare oggetti serializzati utilizzando il <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare il costruttore di serializzazione. Per una classe sealed, rendere il costruttore privato; in caso contrario renderlo protetto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere una violazione della regola. Il tipo non saranno deserializzabile e non funzionerà in molti scenari.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che soddisfa la regola.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>