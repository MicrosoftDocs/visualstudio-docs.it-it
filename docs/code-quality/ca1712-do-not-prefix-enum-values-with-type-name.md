---
title: 'CA1712: Non utilizzare nomi di tipo come prefisso nei valori di enumerazione'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b6d8a5ebba4f746c7418fcfb28a61d98949441e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Non utilizzare nomi di tipo come prefisso nei valori di enumerazione
|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un'enumerazione contiene un membro il cui nome inizia con il nome del tipo dell'enumerazione.

## <a name="rule-description"></a>Descrizione della regola
 I nomi dei membri dell'enumerazione non hanno come prefisso con il nome di tipo perché le informazioni sul tipo è previsto deve essere fornito da strumenti di sviluppo.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce il tempo necessario all'apprendimento di una nuova libreria software, che aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il prefisso del nome tipo del membro di enumerazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente mostra un'enumerazione denominata in modo errato, aggiungendo la versione corretta.

 [!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1711: Gli identificatori non devono contenere un suffisso non corretto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Enum?displayProperty=fullName>