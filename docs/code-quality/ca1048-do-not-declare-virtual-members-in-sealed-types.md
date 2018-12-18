---
title: 'CA1048: Non dichiarare membri virtuali nei tipi sealed'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdd01a1ce610ebd0e2a383ca3eac3a04ffbbdcfb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Non dichiarare membri virtuali nei tipi sealed
|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico è sealed e dichiara un metodo che è sia `virtual` (`Overridable` in Visual Basic) e non finale. Questa regola segnala violazioni per i tipi delegati, che devono seguire questo modello.

## <a name="rule-description"></a>Descrizione della regola
 I tipi dichiarano metodi come virtuali in modo che l'ereditarietà di tipi possa eseguire l'override dell'implementazione del metodo virtuale. Per definizione, è possibile ereditare da un tipo sealed, rendere un metodo virtuale su un tipo sealed non significativo.

 I compilatori Visual Basic e c# non consentono tipi violano questa regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere il metodo non virtuale oppure rendere il tipo ereditabile.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Se si lascia il tipo nel relativo stato corrente può causare problemi di manutenzione e non offre vantaggi.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola questa regola.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]