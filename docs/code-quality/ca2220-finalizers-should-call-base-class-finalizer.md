---
title: 'CA2220: I finalizzatori devono chiamare il finalizzatore della classe base'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 874f0d744f00808d038cdf2bc0343ae7438b76db
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: I finalizzatori devono chiamare il finalizzatore della classe base
|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo che esegue l'override <xref:System.Object.Finalize%2A?displayProperty=fullName> non chiama il <xref:System.Object.Finalize%2A> metodo nella classe base.

## <a name="rule-description"></a>Descrizione della regola
 La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà. A tale scopo, i tipi devono chiamare la relativa classe base <xref:System.Object.Finalize%2A> metodo all'interno di propri <xref:System.Object.Finalize%2A> metodo. Il compilatore c# aggiunge automaticamente la chiamata al finalizzatore della classe base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare il tipo di base <xref:System.Object.Finalize%2A> metodo i <xref:System.Object.Finalize%2A> metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Alcuni compilatori destinati a common language runtime inserire una chiamata al finalizzatore del tipo di base in Microsoft intermediate language (MSIL). Se viene segnalato un avviso da questa regola, il compilatore non inserisce la chiamata e aggiungerla al codice.

## <a name="example"></a>Esempio
 L'esempio di Visual Basic seguente mostra un tipo `TypeB` che chiama correttamente la <xref:System.Object.Finalize%2A> metodo nella classe base.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Vedere anche
 [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)