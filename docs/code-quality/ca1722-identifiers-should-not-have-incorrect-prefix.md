---
title: 'CA1722: Gli identificatori non devono contenere il prefisso non corretto'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c67fef3e9c3b4186b491e624067c1928c2947102
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Gli identificatori non devono contenere il prefisso non corretto
|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un identificatore ha un prefisso non corretto.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, solo determinati elementi di programmazione presentano nomi che iniziano con un prefisso specifico.

 I nomi di tipo non dispone di un prefisso specifico e non devono essere preceduti da "C". Questa regola segnala violazioni per i nomi di tipo, ad esempio "CMyClass" e non segnala violazioni per i nomi dei tipi, ad esempio 'Cache'.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il prefisso dall'identificatore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1715: Gli identificatori devono contenere il prefisso corretto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)