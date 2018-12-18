---
title: 'CA1054: I parametri URI non devono essere stringhe'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98e042d65e0c7530c35134f79357565e1b88f4de
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: I parametri URI non devono essere stringhe
|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo dichiara un metodo con un parametro di stringa il cui nome contiene "uri", "Uri", "urn", "Urn", "url" o "Url" e il tipo non dichiara un overload corrispondente che accetta un <xref:System.Uri?displayProperty=fullName> parametro.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola suddivide il nome del parametro in token in base alla convenzione camel e controlla se ogni token è uguale a "uri", "Uri", "urn", "Urn", "url" o "Url". Se viene trovata una corrispondenza, la regola presuppone che il parametro rappresenta un identificatore di risorsa uniforme (URI). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. Se un metodo accetta una rappresentazione di stringa di un URI, un overload corrispondente deve essere fornito che accetta un'istanza di <xref:System.Uri> (classe), che fornisce questi servizi in modo sicuro e protetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare il parametro per un <xref:System.Uri> digitare; si tratta di una modifica di rilievo. In alternativa, fornire un overload del metodo che accetta un <xref:System.Uri> parametro; si tratta di una modifica non determina interruzione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il parametro non rappresenta un URI.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `ErrorProne`, che viola la regola e un tipo, `SaferWay`, che soddisfa la regola.

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Regole correlate
 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)