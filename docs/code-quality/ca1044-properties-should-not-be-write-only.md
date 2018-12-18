---
title: 'CA1044: Le proprietà non devono essere in sola scrittura'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 204108ed86d37594d7debc0a69139a7f2a28a44a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Le proprietà non devono essere in sola scrittura
|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 La proprietà pubblica o protetta è una funzione di accesso set, ma non dispone di una funzione di accesso get.

## <a name="rule-description"></a>Descrizione della regola
 Ottenere le funzioni di accesso forniscono l'accesso in lettura a una proprietà e funzioni di accesso set forniscono l'accesso in scrittura. Sebbene la presenza di proprietà di sola lettura sia accettabile e spesso necessaria, le linee guida di progettazione proibiscono l'utilizzo di proprietà di sola scrittura. Questo avviene perché consentire a un utente di impostare un valore e quindi impedire all'utente di visualizzare il valore non fornisce alcuna protezione. Inoltre, senza accesso in lettura, lo stato degli oggetti condivisi non può essere visualizzato, il che ne limita l'utilità.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere una funzione di accesso get della proprietà. In alternativa, se il comportamento di una proprietà di sola scrittura è necessario, eseguire la conversione di questa proprietà a un metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È consigliabile che non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `BadClassWithWriteOnlyProperty` è un tipo con una proprietà di sola scrittura. `GoodClassWithReadWriteProperty` contiene il codice corretto.

 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]