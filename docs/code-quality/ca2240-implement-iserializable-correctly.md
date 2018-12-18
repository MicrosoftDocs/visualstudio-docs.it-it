---
title: 'CA2240: Implementare ISerializable in modo corretto'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9929937fa8655e5cbb4c86eebd4dce24fcb26966
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementare ISerializable in modo corretto
|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente è assegnabile al <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia e una delle seguenti condizioni è true:

-   Il tipo eredita ma non esegue l'override di <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metodo e il tipo dichiara i campi di istanza che non siano contrassegnati con il <xref:System.NonSerializedAttribute?displayProperty=fullName> attributo.

-   Il tipo non è bloccato e il tipo implementa un <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo che non è visibile esternamente e sottoponibile a override.

## <a name="rule-description"></a>Descrizione della regola
 Istanza i campi che vengono dichiarati in un tipo che eredita il <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia non sono automaticamente inclusi nel processo di serializzazione. Per includere i campi, il tipo deve implementare il <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo e il costruttore di serializzazione. Se non devono essere serializzati i campi, applicare il <xref:System.NonSerializedAttribute> attributo per i campi da indicare esplicitamente la decisione.

 In tipi non sealed, le implementazioni del <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo deve essere visibile esternamente. Pertanto, il metodo può essere chiamato da tipi derivati e sottoponibile a override.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere il <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo visibile e sottoponibile a override e accertarsi che tutti i campi di istanza siano inclusi nel processo di serializzazione o contrassegnati in modo esplicito con il <xref:System.NonSerializedAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente mostra due tipi serializzabili che violano la regola.

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Esempio
 Nell'esempio seguente consente di correggere le violazioni precedenti due fornendo un'implementazione sottoponibile a override di <xref:System.Runtime.Serialization.ISerializable.GetObjectData> nella classe Book e fornendo un'implementazione di `GetObjectData` nella classe di libreria.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA2236: Chiamare metodi di classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md) [CA2229: implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md) [CA2238: implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md) [ CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md) [CA2237: contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) [CA2239: fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md) [CA2120: proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)
