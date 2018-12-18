---
title: 'CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d46bc7bcfa8c1918091fabbbd759172259ea9ba6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
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
>  **Nota** nelle versioni 2.0 e versioni successive del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], il runtime protegge automaticamente un `try` / `catch` /  `finally` impedire i filtri eccezioni dannoso, se si verifica la reimpostazione direttamente all'interno del metodo che contiene il blocco di eccezioni.

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