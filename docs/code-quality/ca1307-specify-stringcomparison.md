---
title: 'CA1307: Specificare StringComparison | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7087cfe23f7911ec33891a70cd88cf47ee9e4a7b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Specificare StringComparison
|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|Category|Microsoft.Globalization|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un'operazione di confronto tra stringhe utilizza un overload del metodo che non viene impostato un <xref:System.StringComparison> parametro.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Molte operazioni stringa, soprattutto il <xref:System.String.Compare%2A> e <xref:System.String.Equals%2A> metodi, fornire un overload che accetta un <xref:System.StringComparison> come parametro un valore di enumerazione.  
  
 Ogni volta che è presente un overload che accetta un <xref:System.StringComparison> parametro deve essere utilizzato invece di un overload che non accetta il parametro. Impostando questo parametro in modo esplicito, il codice viene spesso diventa più chiaro e facile da gestire.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare i metodi di confronto di stringhe per gli overload che accettano il <xref:System.StringComparison> enumerazione come parametro. Ad esempio: modificare `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è destinata a un pubblico locale limitato e pertanto non sarà localizzata.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)   
 [CA1309: Usare StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)