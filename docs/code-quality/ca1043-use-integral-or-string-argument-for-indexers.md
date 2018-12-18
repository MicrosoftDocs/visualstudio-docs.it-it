---
title: 'CA1043: Utilizzare argomento di tipo stringa o integrale per gli indicizzatori'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91437defeaebddd176dd23732aa40e76522bfeb6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Utilizzare argomento di tipo stringa o integrale per gli indicizzatori
|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene un indicizzatore pubblico o protetto che utilizza un tipo di indice diverso da <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, o <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Gli indicizzatori, ovvero, le proprietà indicizzate, devono utilizzare tipi integer o stringa per l'indice. Questi tipi vengono in genere utilizzati per l'indicizzazione di strutture di dati e aumentano l'utilizzabilità della libreria. Utilizzare il <xref:System.Object> tipo deve essere limitato ai casi in cui il tipo specifico di tipo integer o stringa non può essere specificato in fase di progettazione. Se la progettazione richiede altri tipi per l'indice, verificare che il tipo rappresenta un archivio dati logico. Se non rappresenta un archivio dati logici, utilizzare un metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'indice in un tipo integer o string oppure utilizzare un metodo anziché l'indicizzatore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola solo dopo aver considerato attentamente la necessità per l'indicizzatore non standard.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un indicizzatore che utilizza un <xref:System.Int32> indice.

 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1023: Gli indicizzatori non devono essere multidimensionali](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Usare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)