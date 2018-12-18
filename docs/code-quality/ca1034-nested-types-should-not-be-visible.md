---
title: 'CA1034: I tipi annidati non devono essere visibili | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dc35514eab2344c086305ec88435ff8a32285e4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: I tipi annidati non devono essere visibili
|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo visibile esternamente contiene una dichiarazione di tipo visibile esternamente. Enumerazioni annidate e i tipi protetti non sono interessati da questa regola.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un tipo annidato è un tipo dichiarato all'interno dell'ambito di un altro tipo. I tipi annidati sono utili per incapsulare dettagli di implementazione privati del tipo contenitore. I tipi annidati utilizzati per questo scopo non devono essere visibili esternamente.  
  
 Non utilizzare tipi annidati visibili esternamente per il raggruppamento logico o per evitare conflitti di nomi; Utilizzare invece gli spazi dei nomi.  
  
 I tipi annidati includono la nozione di accessibilità del membro, che non riconosce chiaramente alcuni programmatori.  
  
 Tipi protetti possono essere utilizzati nelle sottoclassi e tipi annidati in scenari di personalizzazione avanzata.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Se non si intende il tipo annidato sia visibile esternamente, modificare l'accessibilità del tipo. In caso contrario, rimuovere il tipo annidato dal relativo elemento padre. Se lo scopo dell'annidamento per classificare il tipo annidato, è possibile utilizzare uno spazio dei nomi per creare la gerarchia invece.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola la regola.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]