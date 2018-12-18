---
title: 'CA1001: I tipi proprietari di campi Disposable devono essere Disposable'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3def21cf32dd45c006045a5301293da2a5d0f70
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: I tipi proprietari di campi Disposable devono essere Disposable
|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale - Se il tipo non è visibile all'esterno dell'assembly.<br /><br /> Sostanziale - Se il tipo è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Una classe dichiara e implementa un campo di istanza che è un <xref:System.IDisposable?displayProperty=fullName> tipo e la classe non implementa <xref:System.IDisposable>.

## <a name="rule-description"></a>Descrizione della regola
 Una classe che implementa il <xref:System.IDisposable> interfaccia per l'eliminazione delle risorse non gestite che possiede. Un campo di istanza che è un <xref:System.IDisposable> tipo indica che il campo proprietario di una risorsa non gestita. Una classe che dichiara un <xref:System.IDisposable> campo indirettamente proprietaria di una risorsa non gestita e deve implementare il <xref:System.IDisposable> interfaccia. Se la classe non direttamente le risorse non gestite, non deve implementare un finalizzatore.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare <xref:System.IDisposable> e dal <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chiamata al metodo di <xref:System.IDisposable.Dispose%2A> metodo del campo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe che viola la regola e una classe che soddisfa la regola implementando <xref:System.IDisposable>. La classe non implementa un finalizzatore poiché la classe non dispone direttamente delle risorse non gestite.

 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA2213: I campi Disposable devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: I tipi delle risorse native devono essere Disposable](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)