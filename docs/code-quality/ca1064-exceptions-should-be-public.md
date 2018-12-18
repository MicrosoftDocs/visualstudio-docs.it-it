---
title: 'CA1064: Le eccezioni devono essere pubbliche'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 73daa2d834342cf9d4759d569cd637661696e34d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Le eccezioni devono essere pubbliche
|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Category|Microsoft.Design|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un'eccezione non pubblica deriva direttamente dalla <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>.

## <a name="rule-description"></a>Descrizione della regola
 È visibile nel relativo ambito interno solo un'eccezione interna. Se l'eccezione si verifica al di fuori dell'ambito interno, può essere rilevata solo tramite l'eccezione di base. Se l'eccezione interna è ereditata da <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>, il codice esterno non contiene informazioni sufficienti per sapere cosa fare con l'eccezione.

 Tuttavia, se il codice dispone di un'eccezione pubblica in un secondo momento viene utilizzata come base per un'eccezione interna, è ragionevole supporre che il codice ulteriormente out sarà in grado di eseguire un'operazione intelligente con l'eccezione di base. Eccezione pubblica sarà disponibili altre informazioni rispetto a quello fornito da <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rendere pubblico il tipo di eccezione o derivare l'eccezione interna da un'eccezione non pubblica <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Esclusione di un messaggio da questa regola se si è certi in tutti i casi l'eccezione privata verrà rilevata nel relativo ambito interno.

## <a name="example"></a>Esempio
 Questa regola funziona sul primo metodo di esempio, FirstCustomException perché la classe di eccezione deriva direttamente da eccezione ed è interna. La regola non viene generato nella classe SecondCustomException perché anche se la classe deriva direttamente da Exception, la classe è dichiarata pubblica. La terza classe inoltre non venga attivato la regola perché non deriva direttamente da <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, o <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
