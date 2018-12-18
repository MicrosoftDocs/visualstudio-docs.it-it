---
title: 'CA2227: Le proprietà di raccolte devono essere in sola lettura'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 486a210b348149823e442ce12befb63e49b08390
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Le proprietà di raccolte devono essere in sola lettura
|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Una proprietà modificabile visibile esternamente è un tipo che implementa <xref:System.Collections.ICollection?displayProperty=fullName>. Set di autorizzazioni, matrici e indicizzatori (proprietà con il nome 'Item') vengono ignorati dalla regola.

## <a name="rule-description"></a>Descrizione della regola
 Una proprietà di raccolta scrivibile consente a un utente di sostituire la raccolta con una raccolta completamente diversa. Una proprietà di sola lettura interrompe la sostituzione della raccolta ma consente ancora l'impostazione dei singoli membri. Se la sostituzione della raccolta è un obiettivo, lo schema progettuale preferito è per includere un metodo per rimuovere tutti gli elementi dalla raccolta e un metodo per ripopolare la raccolta. Vedere il <xref:System.Collections.ArrayList.Clear%2A> e <xref:System.Collections.ArrayList.AddRange%2A> metodi di <xref:System.Collections.ArrayList?displayProperty=fullName> per un esempio di questo modello di classe.

 Serializzazione XML e binaria supportano le proprietà di sola lettura che vengono raccolte. Il <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe presenta requisiti specifici per i tipi che implementano <xref:System.Collections.ICollection> e <xref:System.Collections.IEnumerable?displayProperty=fullName> per poter essere serializzabili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare la proprietà di sola lettura e, se la progettazione, è necessario aggiungere metodi per cancellare e ripopolare la raccolta.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo con una proprietà di raccolta scrivibile e Mostra come la raccolta può essere sostituita direttamente. Inoltre, il modo preferito di sostituzione di una proprietà di raccolta di sola lettura mediante `Clear` e `AddRange` metodi viene visualizzato.

 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Regole correlate
 [CA1819: Le proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md)