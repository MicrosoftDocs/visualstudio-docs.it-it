---
title: 'CA2242: Testare i valori NaN in modo corretto | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords: CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b79c2d180bab62239dcace4bcf5b49195d339946
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testare i valori NaN in modo corretto
|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|Category|Microsoft. Usage|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Testa un valore rispetto a un'espressione <xref:System.Single.NaN?displayProperty=fullName> o <xref:System.Double.NaN?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descrizione della regola  
 <xref:System.Double.NaN?displayProperty=fullName>, che rappresenta un numero non, viene generato quando un'operazione aritmetica è definita. Qualsiasi espressione che verifica l'uguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce sempre `false`. Qualsiasi espressione che consente di verificare la disuguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituisce sempre `true`.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola e determinare se un valore rappresenta <xref:System.Double.NaN?displayProperty=fullName>, utilizzare <xref:System.Single.IsNaN%2A?displayProperty=fullName> o <xref:System.Double.IsNaN%2A?displayProperty=fullName> per testare il valore.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra due espressioni che erroneamente testano un valore rispetto a <xref:System.Double.NaN?displayProperty=fullName> e un'espressione che utilizza correttamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> per testare il valore.  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]