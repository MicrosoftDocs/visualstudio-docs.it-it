---
title: 'CA1047: Non dichiarare membri protetti nei tipi sealed'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f25af4cf9ddd86bd28b5909242ab55f35a467438
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Non dichiarare membri protetti nei tipi sealed
|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Category|Microsoft.Design|
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