---
title: 'CA2208: Creare istanze di eccezioni di argomento correttamente'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab379305eae593a1c2f14f5c2ec860d398af2eaf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Creare istanze di eccezioni di argomento correttamente
|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Possibili cause includono le situazioni seguenti:

-   Viene eseguita una chiamata al costruttore predefinito (senza parametri) di un tipo di eccezione, o che deriva da <xref:System.ArgumentException>.

-   Un argomento stringa non corretto viene passato a un costruttore con parametri di un tipo di eccezione, o che deriva da <xref:System.ArgumentException>.

## <a name="rule-description"></a>Descrizione della regola
 Invece di chiamare il costruttore predefinito, chiamare uno degli overload del costruttore che consente a un messaggio di eccezione più significativo da fornire. Il messaggio di eccezione deve lo sviluppatore di destinazione e spiegare chiaramente la condizione di errore e su come risolvere o evitare l'eccezione.

 Le firme dei costruttori di stringa di uno e due di <xref:System.ArgumentException> e i tipi derivati non sono coerenti con il `message` e `paramName` parametri. Assicurarsi che questi costruttori vengono chiamati con gli argomenti stringa corretti. Le firme sono come segue:

 <xref:System.ArgumentException>(stringa `message`)

 <xref:System.ArgumentException>(stringa `message`, stringa `paramName`)

 <xref:System.ArgumentNullException>(stringa `paramName`)

 <xref:System.ArgumentNullException>(stringa `paramName`, stringa `message`)

 <xref:System.ArgumentOutOfRangeException>(stringa `paramName`)

 <xref:System.ArgumentOutOfRangeException>(stringa `paramName`, stringa `message`)

 <xref:System.DuplicateWaitObjectException>(stringa `parameterName`)

 <xref:System.DuplicateWaitObjectException>(stringa `parameterName`, stringa `message`)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare un costruttore che accetta un messaggio, un nome di parametro o entrambi e assicurarsi che gli argomenti sono appropriati per il tipo di <xref:System.ArgumentException> la chiamata.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola solo se viene chiamato un costruttore con parametri con gli argomenti di stringa corretta.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato il costruttore che crea un'istanza in modo non corretto di un'istanza del tipo ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example"></a>Esempio
 Nell'esempio seguente consente di correggere la violazione precedente scambiando gli argomenti del costruttore.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]