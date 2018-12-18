---
title: "CA1502: Evitare complessità eccessiva | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a643d71e334d7a9228afbb9ba95df2f4cbb558c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Evitare complessità eccessiva
|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|Category|Microsoft.Maintainability|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un metodo presenta una complessità ciclomatica eccessiva.  
  
## <a name="rule-description"></a>Descrizione della regola  
 *Complessità ciclomatica* misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali. In genere, una complessità ciclomatica bassa indica un metodo che è facile da comprendere, testare e gestire. La complessità ciclomatica viene calcolata da un grafico del flusso di controllo del metodo e come indicato di seguito:  
  
 complessità ciclomatica = numero di vertici - il numero di nodi + 1  
  
 in un nodo rappresenta un punto di ramo logico e un bordo rappresenta una riga tra i nodi.  
  
 La regola segnala una violazione quando la complessità ciclomatica è superiore a 25.  
  
 Altre informazioni sulla metrica del codice in [misurazione della complessità e la manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, eseguire il refactoring del metodo per ridurre la complessità ciclomatica.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se non è possibile ridurre facilmente la complessità e il metodo è facile da comprendere, testare e gestire. In particolare, un metodo che contiene una grande `switch` (`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) istruzione è un candidato per l'esclusione. Il rischio di destabilizzare il codice di base del ciclo di sviluppo o di introdurre una modifica imprevista nel comportamento di runtime nel codice fornito in precedenza potrà superano i vantaggi di manutenibilità dal refactoring del codice.  
  
## <a name="how-cyclomatic-complexity-is-calculated"></a>La modalità di calcolo complessità ciclomatica  
 La complessità ciclomatica viene calcolata aggiungendo 1 al seguente:  
  
-   Numero di rami (ad esempio `if`, `while`, e `do`)  
  
-   Numero di `case` le istruzioni in un`switch`  
  
 Gli esempi seguenti mostrano i metodi che presentano vari complessità ciclomatica.  
  
## <a name="example"></a>Esempio  
 **Complessità ciclomatica di 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## <a name="example"></a>Esempio  
 **Complessità ciclomatica di 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## <a name="example"></a>Esempio  
 **Complessità ciclomatica di 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## <a name="example"></a>Esempio  
 **Complessità ciclomatica di 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)