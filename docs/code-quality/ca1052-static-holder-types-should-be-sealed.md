---
title: 'CA1052: I tipi statici devono essere sealed. | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d9ce807aca8b28a279a3a423802196e710f63dea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: I tipi che contengono membri statici devono essere sealed
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo pubblico o protetto contiene solo membri statici e non è dichiarato con la [sealed](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificatore.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola presuppone che un tipo che contiene solo membri statici non è progettato per essere ereditate, perché il tipo non fornisce alcuna funzionalità che possono essere sostituite in un tipo derivato. Un tipo non adatto a essere ereditato deve essere contrassegnato con il `sealed` modificatore per impedirne l'utilizzo come tipo di base.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, contrassegnare il tipo come `sealed`. Se la destinazione è [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 o versione successiva, un approccio migliore consiste nel contrassegnare il tipo come `static`. In questo modo, si evita che dichiarare un costruttore privato per impedire che la creazione della classe.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola solo se il tipo è progettato per essere ereditata. L'assenza del `sealed` modificatore indica che il tipo può essere utilizzato come tipo di base.  
  
## <a name="example-of-a-violation"></a>Esempio di violazione  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente viene illustrato un tipo che viola la regola.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>Risolvere con il modificatore Static  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente viene illustrato come risolvere una violazione di questa regola, contrassegnare il tipo con il `static` modificatore.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1053: I tipi che contengono membri statici non devono avere costruttori](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
