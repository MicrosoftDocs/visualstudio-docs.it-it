---
title: 'CA2240: Implementare ISerializable correttamente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b60f145d31b966ebdc05af975baf5c862cc76251
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementare ISerializable in modo corretto
|||  
|-|-|  
|TypeName|ImplementISerializableCorrectly|  
|CheckId|CA2240|  
|Category|Microsoft. Usage|  
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
 [CA2236: Chiamare metodi della classe base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)  
 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
 [CA2239: Specificare metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)  
