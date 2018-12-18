---
title: 'CA2200: Eseguire il rethrow per conservare i dettagli dello stack'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c43ba2e9f87d19111ceb43708780c0dd2e9e7e39
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Eseguire il rethrow per conservare i dettagli dello stack
|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un'eccezione viene generata nuovamente e l'eccezione è specificato in modo esplicito il `throw` istruzione.

## <a name="rule-description"></a>Descrizione della regola
 Una volta che viene generata un'eccezione, insieme alle informazioni in essa contenute è la traccia dello stack. La traccia dello stack è un elenco della gerarchia di chiamata di metodo che inizia con il metodo che genera l'eccezione e termina con il metodo che intercetta l'eccezione. Se un'eccezione viene generata nuovamente specificando l'eccezione nel `throw` istruzione, la traccia dello stack viene riavviata in corrispondenza del metodo corrente e l'elenco di chiamate al metodo tra il metodo originale che ha generato l'eccezione e il metodo corrente viene perso. Per mantenere le informazioni di traccia dello stack originale con l'eccezione, utilizzare il `throw` istruzione senza specificare l'eccezione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rigenerare l'eccezione senza specificare in modo esplicito l'eccezione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo, `CatchAndRethrowExplicitly`, che viola la regola e un metodo, `CatchAndRethrowImplicitly`, che soddisfa la regola.

 [!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]