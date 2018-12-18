---
title: 'CA1720: Gli identificatori non devono contenere nomi di tipo'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8a981dc4c8ccd016836ea55b2ecd624e781c5a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Gli identificatori non devono contenere nomi di tipo
|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un parametro in un membro visibile esternamente contiene un nome di tipo di dati.

 oppure

 Il nome di un membro visibile esternamente contiene un nome di tipo di dati specifico del linguaggio.

## <a name="rule-description"></a>Descrizione della regola
 Nomi di parametri e membri meglio vengono utilizzati per comunicare il significato di to descrivono il tipo, il quale deve essere fornito dagli strumenti di sviluppo. Per i nomi dei membri, se è necessario utilizzare un nome di tipo di dati, utilizzare un nome indipendente dal linguaggio anziché uno specifico della lingua. Anziché il nome di tipo c# 'int', ad esempio, utilizzare il nome del tipo di dati indipendenti dal linguaggio Int32.

 Ogni token discreti il nome del parametro o un membro viene confrontato con i nomi dei tipi di dati specifico del linguaggio seguenti, in modo tra maiuscole e minuscole:

-   Bool

-   WChar

-   Int8

-   UInt8

-   Short

-   UShort

-   Int

-   UInt

-   Integer

-   UInteger

-   Long

-   ULong

-   Senza segno

-   Firmato

-   Float

-   Float32

-   Float64

 Inoltre, i nomi di parametro vengono inoltre confrontati con i seguenti nomi di tipo di dati indipendenti dal linguaggio e minuscole:

-   Object

-   obj

-   Booleano

-   Char

-   Stringa

-   SByte

-   Byte

-   UByte

-   Int16

-   UInt16

-   Int32

-   UInt32

-   Int64

-   UInt64

-   IntPtr

-   PTR

-   Puntatore

-   UInptr

-   UPtr

-   UPointer

-   Single

-   Double

-   Decimale

-   GUID

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 **Se viene generato con un parametro:**

 Sostituire l'identificatore del tipo di dati del nome del parametro con un termine che meglio descrive il significato o un termine più generico, ad esempio 'value'.

 **Se generato rispetto a un membro:**

 Sostituire l'identificatore del tipo di dati specifico del linguaggio nel nome del membro con un termine che meglio descrive il significato, un equivalente indipendente dal linguaggio o un termine più generico, ad esempio 'value'.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Uso occasionale di nomi di parametro e il membro tipo potrebbe essere appropriato. Tuttavia, per un nuovo sviluppo, non noto possono verificarsi scenari in cui è necessario escludere un avviso da questa regola. Per le librerie fornite in precedenza, potrebbe essere necessario escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)