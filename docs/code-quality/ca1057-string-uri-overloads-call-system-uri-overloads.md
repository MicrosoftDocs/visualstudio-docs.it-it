---
title: 'CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a2e140b4b861e2666350154d861814378f5d115
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri
|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo dichiara overload del metodo che differiscono solo per la sostituzione di un parametro di stringa con un <xref:System.Uri?displayProperty=fullName> parametro e l'overload che accetta il parametro della stringa non chiama l'overload che accetta il <xref:System.Uri> parametro.

## <a name="rule-description"></a>Descrizione della regola
 Perché gli overload differiscono solo per la stringa /<xref:System.Uri> parametro, la stringa si presuppone che rappresenti un uniform resource identifier (URI). Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza. La <xref:System.Uri> classe fornisce questi servizi in modo sicuro e protetto. Per sfruttare i vantaggi del <xref:System.Uri> (classe), è necessario chiamare l'overload della stringa di <xref:System.Uri> overload utilizzando l'argomento stringa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Implementare nuovamente il metodo che usa la rappresentazione di stringa dell'URI in modo che crei un'istanza del <xref:System.Uri> classe usando l'argomento di stringa e quindi passa il <xref:System.Uri> oggetto all'overload che dispone di <xref:System.Uri> parametro.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il parametro della stringa non rappresenta un URI.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un overload di stringa implementato correttamente.

 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)