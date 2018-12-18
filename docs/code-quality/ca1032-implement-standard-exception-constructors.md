---
title: 'CA1032: Implementare costruttori di eccezioni standard'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d140ab9f9ee5ef27332c59e30920fa89aebefdde
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementare costruttori di eccezioni standard
|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Estende un tipo <xref:System.Exception?displayProperty=fullName> e dichiara tutti i costruttori necessari.

## <a name="rule-description"></a>Descrizione della regola
 Tipi di eccezione devono implementare i seguenti costruttori:

-   NewException() pubblica

-   NewException(string) pubblica

-   pubblica NewException (string, eccezione)

-   NewException protetto o privato (SerializationInfo, StreamingContext)

 Se non viene fornito l'insieme completo di costruttori può risultare difficile gestire correttamente le eccezioni. Ad esempio, il costruttore con la firma `NewException(string, Exception)` viene utilizzato per creare le eccezioni causate da altre eccezioni. Senza questo costruttore non è possibile creare e generare un'istanza di eccezione personalizzata che contiene un'eccezione (annidata) interna, che è necessario eseguire l'operazione per il codice gestito in tale situazione. I primo tre costruttori di eccezioni sono pubblici per convenzione. Il quarto costruttore è protetto nelle classi non sealed e privato nelle classi sealed. Per altre informazioni, vedere [CA2229: implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere i costruttori mancanti all'eccezione e assicurarsi che dispongano di accessibilità corretta.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la violazione è causata dall'utilizzo di un livello di accesso diversi per i costruttori pubblici.

## <a name="example"></a>Esempio
 Nell'esempio seguente contiene un tipo di eccezione che viola la regola e un tipo di eccezione che viene implementato correttamente.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]