---
title: ': Ca2119 impostare metodi che soddisfano interfacce private | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b61a3e81ff7be1ff868f2dd9ce42dd5cb10522cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Impostare come sealed i metodi che soddisfano interfacce private
|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo pubblico ereditabile fornisce un'implementazione di metodo sottoponibile a override di un `internal` (`Friend` in Visual Basic) dell'interfaccia.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Metodi di interfaccia avere accessibilità pubblica, che può essere modificata dal tipo di implementazione. Un'interfaccia interna crea un contratto che non deve essere implementato all'esterno dell'assembly che definisce l'interfaccia. Un tipo pubblico che implementa un metodo di un'interfaccia interna mediante il `virtual` (`Overridable` in Visual Basic) consente di modificatore del metodo da sottoporre a override da un tipo derivato è all'esterno dell'assembly. Se un secondo tipo nell'assembly di definizione chiama il metodo e prevede un contratto solo interno, comportamento può essere compromessi, quando il metodo sottoposto a override nell'assembly esterno viene invece eseguito. Crea una vulnerabilità di sicurezza.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, impedire che il metodo sottoposto all'esterno dell'assembly utilizzando uno dei valori seguenti:  
  
-   Rendere il tipo dichiarante `sealed` (`NotInheritable` in Visual Basic).  
  
-   Modificare l'accessibilità per il tipo dichiarante `internal` (`Friend` in Visual Basic).  
  
-   Rimuovere tutti i costruttori pubblici del tipo dichiarante.  
  
-   Implementare il metodo senza utilizzare il `virtual` modificatore.  
  
-   Implementare il metodo in modo esplicito.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È consigliabile escludere un avviso da questa regola se dopo un'attenta analisi, nessun problema di sicurezza che potrebbe essere vulnerabile se il metodo viene sottoposto a override all'esterno dell'assembly.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo, `BaseImplementation`, che violano questa regola.  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene sfrutta l'implementazione del metodo virtuale dell'esempio precedente.  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce](/dotnet/csharp/programming-guide/interfaces/index)   
 [Interfacce](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)