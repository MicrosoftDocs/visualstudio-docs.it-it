---
title: 'CA2124: Eseguire il wrapping vulnerabile infine clausole esterno try | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 567c519b09042dbd0bba447d4631544dd78ca1ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno
|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|Category|Microsoft.Security|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Nelle versioni 1.0 e 1.1 del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], un metodo pubblico o protetto contiene un `try` / `catch` / `finally` blocco. Il `finally` blocco per lo stato di sicurezza e non è incluso in un `finally` blocco.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola individua `try` / `finally` blocchi nel codice destinato alle versioni 1.0 e 1.1 del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] che potrebbero essere vulnerabili a filtri di eccezioni dannoso presenti nello stack di chiamate. Se vengono eseguite operazioni, ad esempio la rappresentazione nel blocco try e viene generata un'eccezione, il filtro può essere eseguito prima il `finally` blocco. Nell'esempio della rappresentazione, ciò significa che il filtro verrebbe eseguito come utente rappresentato. I filtri sono attualmente implementabili solo in Visual Basic.  
  
> [!WARNING]
>  **Nota** nelle versioni 2.0 e versioni successive del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], il runtime protegge automaticamente un `try` / `catch` /  `finally` impedire i filtri di eccezioni dannoso, se si verifica il ripristino direttamente all'interno del metodo che contiene il blocco di eccezioni.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Posizionare il wrapping `try` / `finally` in un blocco try esterno. Vedere il secondo esempio che segue. In questo modo il `finally` da eseguire prima il codice del filtro.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="pseudo-code-example"></a>Esempio di pseudocodice  
  
### <a name="description"></a>Descrizione  
 Lo pseudocodice seguente illustra il modello rilevato da questa regola.  
  
### <a name="code"></a>Codice  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## <a name="example"></a>Esempio  
 Lo pseudocodice seguente viene illustrato il modello che è possibile utilizzare per proteggere il codice e soddisfa questa regola.  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```