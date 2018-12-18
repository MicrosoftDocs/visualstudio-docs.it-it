---
title: 'CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bbd12d09c95f1ec93c7232901270cfbece311693
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura
|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|Category|Microsoft.Security|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un tipo visibile esternamente contiene un campo in sola lettura visibile esternamente che costituisce un tipo di riferimento modificabile.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un tipo modificabile è un tipo i cui dati di istanza possono essere modificati. La <xref:System.Text.StringBuilder?displayProperty=fullName> classe è un esempio di un tipo di riferimento modificabile. Contiene membri che è possono modificare il valore di un'istanza della classe. Un esempio di un tipo di riferimento non modificabile è la <xref:System.String?displayProperty=fullName> classe. Dopo che è stata creata un'istanza, il relativo valore non può mai modificato.  
  
 Il modificatore di sola lettura ([readonly](/dotnet/csharp/language-reference/keywords/readonly) in c#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], e [const](/cpp/cpp/const-cpp) in C++) su un tipo di riferimento campo (puntatore in C++) impedisce il campo sostituito da un'altra istanza del tipo di riferimento. Tuttavia, il modificatore non evitare che i dati dell'istanza del campo venga modificato tramite il tipo di riferimento.  
  
 Sola lettura sono interessati da questa regola, ma causano invece una violazione del [CA2105: i campi di matrici non devono essere solo lettura](../code-quality/ca2105-array-fields-should-not-be-read-only.md) regola.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il modificatore di sola lettura o, se una modifica sostanziale è accettabile, è possibile sostituire il campo con un tipo non modificabile.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se il tipo di campo non è modificabile.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata una dichiarazione di campo che causa una violazione di questa regola.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]