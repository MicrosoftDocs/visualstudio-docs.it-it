---
title: 'CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71a8f96d55c151ef1d6ec42969dd4c08765ec206
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole
|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Category|Microsoft.Naming|
|Modifica importante|Sostanziale - Quando generato su assembly, spazi dei nomi, tipi, membri e parametri.<br /><br /> Non sostanziale - Quando generato su parametri di tipo generico.|

## <a name="cause"></a>Causa
 Il nome di un identificatore non è definito correttamente.

 \- oppure -

 Il nome di un identificatore contiene un acronimo di due lettere e la seconda lettera è in minuscola.

 \- oppure -

 Il nome di un identificatore contiene un acronimo di tre o più lettere maiuscole.

## <a name="rule-description"></a>Descrizione della regola
 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

 Per convenzione, i nomi di parametro utilizzano sulla convenzione camel; i nomi dello spazio dei nomi, tipo e membro utilizzano la convenzione Pascal maiuscole e minuscole. In un nome di maiuscole/minuscole camel, la prima lettera è in minuscola e la prima lettera di tutte le rimanenti parole nel nome è in lettere maiuscole. Esempi di nomi di maiuscole/minuscole camel sono "packetSniffer", "ioFile" e "fatalErrorCode". È in maiuscola la prima lettera in base alla convezione Pascal un nome e la prima lettera di tutte le rimanenti parole nel nome è in lettere maiuscole. Esempi di nomi di base alla convezione Pascal sono "PacketSniffer", "IOFile" e "FatalErrorCode".

 Questa regola divide il nome in parole in base alle maiuscole e minuscole e controlla le parole di due lettere con un elenco di parole comuni di due lettere, ad esempio "In" o "My". Se non viene trovata una corrispondenza, la parola è considerata un acronimo. Inoltre, la regola presuppone che è stato individuato un acronimo quando il nome contiene quattro lettere maiuscole in una riga o tre lettere maiuscole in una riga alla fine del nome.

 Per convenzione, gli acronimi di due lettere utilizzano tutte lettere maiuscole e gli acronimi di tre o più caratteri Pascal maiuscole e minuscole. L'esempio seguente usa questa convenzione di denominazione: "DB", "CR", "Cpa" e "Ecma". I seguenti esempi violano la convenzione: "Io", "XML" e "DoD" e per i nomi, "xp" e "cpl".

 'ID' è maiuscole/minuscole speciale per causare una violazione di questa regola. 'ID' non è un acronimo bensì l'abbreviazione di 'identification'.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare il nome in modo che si è maiuscole e minuscole.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare questo avviso se si dispone di convenzioni di denominazione personalizzate o se l'identificatore rappresenta un nome appropriato, ad esempio, il nome di una società o una tecnologia.

 È anche possibile aggiungere termini specifici e le abbreviazioni gli acronimi che a un dizionario personalizzato di analisi codice. Termini specificati nel dizionario personalizzato non provocheranno violazioni di questa regola. Per altre informazioni, vedere [procedura: personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>Regole correlate
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)