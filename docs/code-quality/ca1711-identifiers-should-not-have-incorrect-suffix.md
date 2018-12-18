---
title: 'CA1711: Gli identificatori non devono contenere un suffisso non corretto'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13160a8056c8fb4ec824d84c132fe87a7b565f27
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: Gli identificatori non devono contenere un suffisso non corretto
|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un identificatore ha un suffisso non corretto.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, solo i nomi dei tipi che estendono determinati tipi di base o che implementano determinate interfacce o dei tipi derivati da questi tipi devono terminare con suffissi specifici riservati. Gli altri nomi di tipi non devono utilizzare questi suffissi riservati.

 Nella tabella seguente sono elencati i suffissi riservati e i tipi base e interfacce a cui sono associate.

|Suffisso|Interfaccia di tipo di base|
|------------|--------------------------|
|Attributo|<xref:System.Attribute?displayProperty=fullName>|
|Raccolta|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Dizionario|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|Un delegato del gestore di evento|
|Eccezione|<xref:System.Exception?displayProperty=fullName>|
|Autorizzazioni|<xref:System.Security.IPermission?displayProperty=fullName>|
|Coda|<xref:System.Collections.Queue?displayProperty=fullName>|
|Stack|<xref:System.Collections.Stack?displayProperty=fullName>|
|Flusso|<xref:System.IO.Stream?displayProperty=fullName>|

 Inoltre, i seguenti suffissi devono **non** utilizzare:

-   delegato

-   Enum

-   Impl - utilizzare invece 'Base'

-   Ex o suffisso analogo per distinguerlo da una versione precedente dello stesso tipo

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il suffisso dal nome del tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola a meno che il suffisso abbia un significato ambiguo nel dominio dell'applicazione.

## <a name="related-rules"></a>Regole correlate
 [CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>Vedere anche
 [Gli attributi](/dotnet/standard/design-guidelines/attributes) [gestione e generazione di eventi](/dotnet/standard/events/index)