---
title: 'CA1056: Le proprietà URI non devono essere stringhe'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e1f28bf1dc0829b80c53aface1c11de2b44cdbb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: Le proprietà URI non devono essere stringhe
|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo dichiara una proprietà stringa il cui nome contiene "uri", "Uri", "urn", "Urn", "url" o "Url".

## <a name="rule-description"></a>Descrizione della regola
 Questa regola suddivide il nome della proprietà in token in base alla convenzione Pascal e controlla se ogni token è uguale a "uri", "Uri", "urn", "Urn", "url" o "Url". Se viene trovata una corrispondenza, la regola presuppone che la proprietà rappresenta un identificatore di risorsa uniforme (URI). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. La <xref:System.Uri?displayProperty=fullName> classe fornisce questi servizi in modo sicuro e protetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare la proprietà su un <xref:System.Uri> tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se la proprietà non rappresenta un URI.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `ErrorProne`, che viola la regola e un tipo, `SaferWay`, che soddisfa la regola.

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Regole correlate
 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)