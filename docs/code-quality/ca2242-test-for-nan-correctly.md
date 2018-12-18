---
title: 'CA2242: Testare i valori NaN in modo corretto'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c87b3e3528f12c07f728a5b82b56e75ee6551c1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testare i valori NaN in modo corretto
|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Testa un valore rispetto a un'espressione <xref:System.Single.NaN?displayProperty=fullName> o <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Double.NaN?displayProperty=fullName>, che rappresenta non un numero, si verifica quando un'operazione aritmetica è definita. Qualsiasi espressione che verifica l'uguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce sempre `false`. Qualsiasi espressione che consente di verificare la disuguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce sempre `true`.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola e determinare se un valore rappresenta <xref:System.Double.NaN?displayProperty=fullName>, utilizzare <xref:System.Single.IsNaN%2A?displayProperty=fullName> o <xref:System.Double.IsNaN%2A?displayProperty=fullName> per testare il valore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente mostra due espressioni che erroneamente testano un valore rispetto a <xref:System.Double.NaN?displayProperty=fullName> e un'espressione che utilizza correttamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> per testare il valore.

 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]