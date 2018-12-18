---
title: 'CA2215: I metodi Dispose devono chiamare dispose della classe base | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 791de4f70113df3759e920591ec94da5108eec9a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base
|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Categoria|Microsoft. Usage|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> eredita da un tipo che implementa anche <xref:System.IDisposable>. Il <xref:System.IDisposable.Dispose%2A> non chiamata al metodo del tipo che ereditano il <xref:System.IDisposable.Dispose%2A> metodo del tipo padre.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Se un tipo eredita da un tipo eliminabile, deve chiamare il <xref:System.IDisposable.Dispose%2A> metodo del tipo di base dall'interno del proprio <xref:System.IDisposable.Dispose%2A> metodo. La chiamata al metodo del tipo di base Dispose garantisce che tutte le risorse create dal tipo di base vengono rilasciate.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare `base`.<xref:System.IDisposable.Dispose%2A> nel <xref:System.IDisposable.Dispose%2A> metodo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È consigliabile escludere un avviso da questa regola se la chiamata a `base`.<xref:System.IDisposable.Dispose%2A> si verifica un livello più profondo chiamante rispetto a quanto controllato dalla regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable>.  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo `TypeB` che eredita dal tipo `TypeA` e chiama correttamente la <xref:System.IDisposable.Dispose%2A> metodo.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)