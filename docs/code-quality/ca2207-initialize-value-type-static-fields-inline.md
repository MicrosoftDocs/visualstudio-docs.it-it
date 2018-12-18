---
title: 'CA2207: Inizializzare i campi statici dei tipi di valore inline'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a05dda7678fe4a468f3674cbbb1a401a8612df2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inizializzare i campi statici dei tipi di valore inline
|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo di valore dichiara un costruttore statico esplicito.

## <a name="rule-description"></a>Descrizione della regola
 Quando viene dichiarato un tipo di valore, viene sottoposto a un'inizializzazione predefinita in tutti i campi di tipo di valore sono impostati su zero e tutti i campi di tipo di riferimento sono impostati su `null` (`Nothing` in Visual Basic). Un costruttore statico esplicito è garantito solo da eseguire prima di un costruttore di istanza o viene chiamato un membro statico del tipo. Pertanto, se il tipo viene creato senza chiamare un costruttore di istanza, il costruttore statico non è garantito per l'esecuzione.

 Se tutti i dati statici vengono inizializzati inline e non viene dichiarato alcun costruttore statico esplicito, i compilatori c# e Visual Basic aggiungono la `beforefieldinit` flag per la definizione di classe MSIL. Inoltre, i compilatori di aggiungono un costruttore statico privato che contiene il codice di inizializzazione statica. Questo costruttore statico privato è garantito da eseguire prima tutti i campi statici del tipo sono accessibili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando viene dichiarato e rimuovere il costruttore statico.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1810: Inizializzare i campi statici del tipo di riferimento inline](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)