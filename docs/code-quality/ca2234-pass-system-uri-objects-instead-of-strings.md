---
title: 'CA2234: Passare oggetti System.Uri invece di stringhe'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07e0bbaa05b0674666a7d4403daeeee8b23348be
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Passare oggetti System.Uri invece di stringhe
|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Viene eseguita una chiamata a un metodo che presenta un parametro di stringa il cui nome contiene "uri", "Uri", "urn", "Urn", "url" o "Url"; e il tipo dichiarante del metodo contiene un overload del metodo corrispondente con un <xref:System.Uri?displayProperty=fullName> parametro.

## <a name="rule-description"></a>Descrizione della regola
 Un nome di parametro è suddiviso in token in base alla convenzione camel, e quindi ogni token viene controllato per verificare se è uguale a "uri", "Uri", "urn", "Urn", "url" o "Url". Se viene trovata una corrispondenza, si presuppone che il parametro rappresenti un uniform resource identifier (URI). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. La <xref:System.Uri> classe fornisce questi servizi in modo sicuro e protetto. Quando è presente una scelta tra i due overload che differiscono solo per quanto riguarda la rappresentazione di un URI, l'utente deve scegliere l'overload che accetta un <xref:System.Uri> argomento.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare l'overload che accetta il <xref:System.Uri> argomento.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il parametro della stringa non rappresenta un URI.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo, `ErrorProne`, che viola la regola e un metodo, `SaferWay`, che chiama correttamente la <xref:System.Uri> rapporto di overload.

 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)