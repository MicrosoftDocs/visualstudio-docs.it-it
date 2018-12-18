---
title: 'CA1008: Gli enum devono avere valore zero'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4109bf7b455c7a77daa5b9d31b6fe1286cf69c77
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Gli enum devono avere valore zero
|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale - Quando viene richiesto di aggiungere un **Nessuno** valore a un'enumerazione non flag. Sostanziale - Quando viene richiesto di rinominare o rimuovere eventuali valori di enumerazione.|

## <a name="cause"></a>Causa
 Un'enumerazione senza un applicato <xref:System.FlagsAttribute?displayProperty=fullName> non definisce un membro che presenta un valore pari a zero; o un'enumerazione con un applicato <xref:System.FlagsAttribute> definisce un membro che ha un valore pari a zero, ma non è 'None' o l'enumerazione definisce multiple con valori zero membri.

## <a name="rule-description"></a>Descrizione della regola
 Il valore predefinito di un'enumerazione non inizializzata, come altri tipi di valore è zero. Un'enumerazione senza attributi flag definisce un membro con valore pari a zero, in modo che il valore predefinito è un valore valido dell'enumerazione. Se appropriato, denominare il membro 'None'. In caso contrario, assegnare zero al membro utilizzato più di frequente. Si noti che, per impostazione predefinita, se il valore del primo membro di enumerazione non è impostato nella dichiarazione, il valore è zero.

 Se un'enumerazione con la <xref:System.FlagsAttribute> applicato definisce un membro con valore zero, il relativo nome deve essere 'None' per indicare che è stato impostato alcun valore nell'enumerazione. Utilizzando un membro con valore zero per altri scopi sono contrario all'utilizzo del <xref:System.FlagsAttribute> in AND e OR operatori bit per bit sono inutili con il membro. Ciò implica che solo un membro deve essere assegnato il valore zero. Si noti che se più membri con valore zero si verifica in un'enumerazione con attributi flag, `Enum.ToString()` restituisce risultati non corretti per i membri che non sono uguali a zero.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola per le enumerazioni senza attributi flag, definire un membro con valore pari a 0. si tratta di una modifica. Per le enumerazioni con attributi flag che definiscono un membro con valore zero, denominare il membro 'None' ed eliminare eventuali altri membri che hanno un valore pari a zero; si tratta di una modifica di rilievo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola per enumerazioni con attributi flag fornite in precedenza.

## <a name="example"></a>Esempio
 L'esempio seguente mostra due enumerazioni che soddisfano la regola e un'enumerazione, `BadTraceOptions`, che viola la regola.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Non usare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: L'archivio di enum deve essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Enum?displayProperty=fullName>