---
title: 'CA1715: Gli identificatori devono contenere il prefisso corretto'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b4ddef7b6a9ae7eafb6c169ec9e07e89e20fc6b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Gli identificatori devono contenere il prefisso corretto
|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Category|Microsoft.Naming|
|Breaking Change|Sostanziale - Quando generato su interfacce.<br /><br /> Non sostanziale - Quando generato su parametri di tipo generico.|

## <a name="cause"></a>Causa
 Il nome di un'interfaccia visibile esternamente non inizia con una "I" maiuscola.

 oppure

 Il nome di un parametro di tipo generico su un metodo o un tipo visibile esternamente non inizia con una maiuscola ' T' '.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, i nomi di determinati elementi di programmazione iniziano con un prefisso specifico.

 Nomi di interfaccia devono iniziare con una lettera maiuscola 'I' seguito da un'altra lettera maiuscola. Questa regola segnala violazioni per i nomi di interfaccia, ad esempio "MyInterface" e "IsolatedInterface".

 I nomi dei parametri di tipo generico deve iniziare con una maiuscola ' e, facoltativamente, può essere seguita da un'altra lettera maiuscola. Questa regola segnala violazioni per i nomi dei parametri di tipo generico, ad esempio "V" e 'Type'.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rinominare l'identificatore il prefisso corretto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 **Nell'esempio seguente viene illustrata un'interfaccia denominata in modo errato.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

## <a name="example"></a>Esempio
 **Nell'esempio seguente consente di correggere la violazione precedente anteponendo l'interfaccia con 'I'.**

 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="example"></a>Esempio
 **Nell'esempio seguente viene illustrato un parametro di tipo generico denominata in modo errato.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

## <a name="example"></a>Esempio
 **Nell'esempio seguente consente di correggere la violazione precedente aggiungendo il parametro di tipo generico ' T' '.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1722: Gli identificatori non devono contenere il prefisso non corretto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)