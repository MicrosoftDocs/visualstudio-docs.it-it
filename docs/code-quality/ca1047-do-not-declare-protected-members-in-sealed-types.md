---
title: 'CA1047: Non dichiarare membri protetti nei tipi sealed | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f0efeaadbcaa4d13aed8eac236c261caa694534d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Non dichiarare membri protetti nei tipi sealed
|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|Category|Microsoft. Design|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 È un tipo pubblico `sealed` (`NotInheritable` in Visual basic) e dichiara un membro protetto o un tipo annidato protetto. Questa regola segnala violazioni per <xref:System.Object.Finalize%2A> metodi, che devono seguire questo modello.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I tipi dichiarano membri protetti in modo che i tipi che ereditano possano accedere al membro o eseguirne l'override. Per definizione, è possibile ereditare da un tipo sealed, il che significa che i metodi protetti su tipi sealed non può essere chiamato.  
  
 Il compilatore c# genera un avviso per questo errore.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, impostare il livello di accesso del membro privato, oppure rendere il tipo ereditabile.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola. Se si lascia il tipo nel relativo stato corrente può causare problemi di manutenzione e non offre vantaggi.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola questa regola.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]