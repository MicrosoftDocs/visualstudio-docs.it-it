---
title: 'CA1023: Gli indicizzatori non devono essere multidimensionali'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 876eb79237b843721b71a1879cfbb83e7a9918db
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Gli indicizzatori non devono essere multidimensionali
|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene un indicizzatore pubblico o protetto che utilizza più di un indice.

## <a name="rule-description"></a>Descrizione della regola
 Gli indicizzatori, ovvero, le proprietà indicizzate, devono utilizzare un indice singolo. Gli indicizzatori multidimensionali possono ridurre sensibilmente l'usabilità della libreria. Se il progetto richiede più indici, valutare se il tipo rappresenta un archivio dati logico. In caso contrario, utilizzare un metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la progettazione per utilizzare un solo integer o un indice stringa o utilizzare un metodo anziché l'indicizzatore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola solo dopo aver considerato attentamente la necessità per l'indicizzatore non standard.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `DayOfWeek03`, con un indicizzatore multidimensionale che viola la regola. L'indicizzatore può essere considerato come un tipo di conversione e pertanto in modo più appropriato viene esposto come un metodo. Il tipo è stato riprogettato `RedesignedDayOfWeek03` per soddisfare la regola.

 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1043: Usare argomento di tipo stringa o integrale per gli indicizzatori](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Usare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)