---
title: 'CA1813: Evitare attributi non sealed'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b861591355a47d38beec921a13643841b40e4465
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Evitare attributi non sealed
|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Category|Microsoft.Performance|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico eredita da <xref:System.Attribute?displayProperty=fullName>, non è astratta e non è bloccato (`NotInheritable` in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola
 La libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] fornisce metodi per recuperare attributi personalizzati. Per impostazione predefinita, questi metodi eseguono ricerche la gerarchia di ereditarietà di attributo. ad esempio <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> Cerca il tipo di attributo specificato o qualsiasi tipo di attributo che estende il tipo di attributo specificato. Utilizzo di attributi sealed Elimina la ricerca nella gerarchia di ereditarietà e può migliorare le prestazioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere sealed il tipo di attributo o renderlo astratta.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola. Eseguire questa operazione solo se si sta definendo una gerarchia dell'attributo e non può bloccare l'attributo o renderlo astratta.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un attributo personalizzato che soddisfa questa regola.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Contrassegnare gli attributi con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Vedere anche
 [Attributi](/dotnet/standard/design-guidelines/attributes)