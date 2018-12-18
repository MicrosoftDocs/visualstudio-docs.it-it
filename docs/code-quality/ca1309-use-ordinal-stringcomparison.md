---
title: 'CA1309: Utilizza StringComparison ordinale | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cf913eea3f156595c9b9194b3d8a74e71b848367
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Utilizza StringComparison ordinale
|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|Category|Microsoft.Globalization|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Non è impostata un'operazione di confronto di stringhe tra il <xref:System.StringComparison> parametro a **ordinale** o **OrdinalIgnoreCase**.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Molte operazioni stringa, soprattutto il <xref:System.String.Compare%2A?displayProperty=fullName> e <xref:System.String.Equals%2A?displayProperty=fullName> metodi forniscono ora un overload che accetta un <xref:System.StringComparison?displayProperty=fullName> come parametro un valore di enumerazione.  
  
 Quando si specifica **StringComparison. Ordinal** o **StringComparison. OrdinalIgnoreCase**, sarà tra il confronto tra stringhe. Le funzionalità specifiche del linguaggio naturale, ovvero vengono ignorate quando vengono prese decisioni di confronto. Ciò significa che le decisioni sono basate su confronti di byte semplici e ignorare le tabelle di maiuscole e minuscole o di equivalenza parametrizzate dalle impostazioni cultura. Di conseguenza, impostando in modo esplicito il parametro a uno di **StringComparison. Ordinal** o **StringComparison. OrdinalIgnoreCase**, il codice spesso snellire, aumenta la correttezza e diventa più affidabile.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il metodo di confronto di stringhe a un overload che accetta il <xref:System.StringComparison?displayProperty=fullName> enumerazione come parametro e specificare il parametro **ordinale** o **OrdinalIgnoreCase**. Ad esempio, modificare `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è destinata a per un pubblico locale limitato o quando la semantica della lingua corrente deve essere utilizzata.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)   
 [CA1307: Specificare StringComparison](../code-quality/ca1307-specify-stringcomparison.md)