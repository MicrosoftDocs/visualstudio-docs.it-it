---
title: 'CA1821: Rimuovere i finalizzatori vuoti'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccd6ca16dc8a4ca2ce2f2883958ed82fa1c4b3ba
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Rimuovere i finalizzatori vuoti
|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo implementa un finalizzatore, è vuoto, chiama solo il finalizzatore del tipo di base o chiama solo metodi emessi in modo condizionale.

## <a name="rule-description"></a>Descrizione della regola
 Quando possibile, evitare di utilizzare i finalizzatori per non sovraccaricare ulteriormente le prestazioni durante il rilevamento della durata dell'oggetto. Prima di raccogliere l'oggetto, il garbage collector eseguirà il finalizzatore. Ciò significa che due raccolte sono necessarie per raccogliere l'oggetto. Un finalizzatore vuoto provoca questo sovraccarico senza alcun vantaggio.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il finalizzatore vuoto. Se un finalizzatore è richiesto per il debug, racchiudere l'intero finalizzatore in `#if DEBUG / #endif` direttive.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un messaggio da questa regola. Impossibile eliminare la finalizzazione riduce le prestazioni e non offre alcun vantaggio.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un finalizzatore vuoto che deve essere rimosso, un finalizzatore che deve essere racchiusi tra `#if DEBUG / #endif` direttive e un finalizzatore che utilizza il `#if DEBUG / #endif` direttive correttamente.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]