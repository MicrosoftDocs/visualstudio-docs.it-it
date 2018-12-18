---
title: 'CA1026: Non utilizzare i parametri predefiniti | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 43f83bf88e017da06ee3653019aa91807229d55e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Evitare l'utilizzo di parametri predefiniti
|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|CheckId|CA1026|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo visibile esternamente contiene un metodo visibile esternamente che utilizza un parametro predefinito.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I metodi che utilizzano parametri predefiniti sono consentiti con la specifica CLS (Common Language); Tuttavia, la specifica CLS consente ai compilatori di ignorare i valori assegnati a questi parametri. Il codice scritto per compilatori che ignorano i valori predefiniti dei parametri deve fornire esplicitamente gli argomenti per ogni parametro predefinito. Per mantenere il comportamento desiderato tra diversi linguaggi di programmazione, è necessario sostituire i metodi che utilizzano parametri predefiniti con overload che forniscono i parametri predefiniti.  
  
 Durante l'accesso al codice gestito, il compilatore ignora i valori dei parametri predefiniti per estensioni gestite per C++. Il compilatore Visual Basic supporta metodi che presentano i parametri predefiniti che utilizzano il [facoltativo](/dotnet/visual-basic/language-reference/modifiers/optional) (parola chiave).  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire il metodo che utilizza i parametri predefiniti con overload che forniscono i parametri predefiniti.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un metodo che utilizza i parametri predefiniti e i metodi di overload che forniscono una funzionalità equivalente.  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1025: Sostituire gli argomenti ripetitivi con una matrice di parametri](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](/dotnet/standard/language-independence-and-language-independent-components)