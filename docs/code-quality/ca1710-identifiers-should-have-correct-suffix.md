---
title: 'CA1710: Gli identificatori devono contenere il suffisso corretto'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e227676c4af6c864e2830a2d08c70cce08dabfe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Gli identificatori devono contenere il suffisso corretto
|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un identificatore non dispone del suffisso corretto.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, i nomi dei tipi che estendono determinati tipi di base o che implementano determinate interfacce o dei tipi derivati da questi tipi hanno un suffisso associato al tipo di base o interfaccia.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

 Nella tabella seguente sono elencati i tipi di base e interfacce che sono associati suffissi.

|Interfaccia di tipo di base|Suffisso|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Attributo|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Eccezione|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Raccolta|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dizionario|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Raccolta|
|<xref:System.Collections.Queue?displayProperty=fullName>|Raccolta o una coda|
|<xref:System.Collections.Stack?displayProperty=fullName>|Raccolta o Stack|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Raccolta|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dizionario|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Raccolta o DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Flusso|
|<xref:System.Security.IPermission?displayProperty=fullName>|Autorizzazioni|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condizione|
|Un delegato del gestore eventi.|EventHandler|

 I tipi che implementano <xref:System.Collections.ICollection> e sono un tipo generalizzato di struttura di dati, ad esempio un dizionario, stack o coda, sono consentiti nomi che fornisce informazioni significative relative all'utilizzo previsto del tipo.

 I tipi che implementano <xref:System.Collections.ICollection> e sono una raccolta di elementi specifici presentano nomi che terminano con la parola "Collection". Ad esempio, una raccolta di <xref:System.Collections.Queue> oggetti avrebbe il nome "QueueCollection". Il suffisso 'Collection' indica che i membri della raccolta possono essere enumerati utilizzando il `foreach` (`For Each` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) istruzione.

 I tipi che implementano <xref:System.Collections.IDictionary> presentano nomi che terminano con la parola "Dictionary" anche se il tipo implementa inoltre <xref:System.Collections.IEnumerable> o <xref:System.Collections.ICollection>. Le convenzioni di denominazione suffisso "Collection" e "Dictionary" consentono di distinguere tra i seguenti due modelli di enumerazione.

 Tipi con il suffisso 'Collection' seguono questo modello di enumerazione.

```
foreach(SomeType x in SomeCollection) { }
```

 Tipi con il suffisso "Dictionary" seguono questo modello di enumerazione.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Oggetto <xref:System.Data.DataSet> oggetto è costituito da una raccolta di <xref:System.Data.DataTable> oggetti che sono costituiti da raccolte di <xref:System.Data.DataColumn?displayProperty=fullName> e <xref:System.Data.DataRow?displayProperty=fullName> oggetti, tra gli altri. Queste raccolte implementano <xref:System.Collections.ICollection> tramite la base <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> classe.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rinominare il tipo in modo da utilizzare come suffisso il termine corretto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È consigliabile escludere un avviso da utilizzare il suffisso "Collection" se il tipo è una struttura di dati generalizzata che può essere estesa o che conterrà un set arbitrario di elementi diversi. In questo caso, un nome che fornisce informazioni significative sull'implementazione, prestazioni o altre caratteristiche della struttura di dati potrebbe BinaryTree (ad esempio,). Nei casi in cui il tipo rappresenta una raccolta di un tipo specifico (ad esempio StringCollection), non escludere un avviso da questa regola perché il suffisso indica che il tipo può essere enumerato utilizzando un `foreach` istruzione.

 Per gli altri suffissi, non escludere un avviso da questa regola. Il suffisso consente l'utilizzo previsto sia evidente dal nome del tipo.

## <a name="related-rules"></a>Regole correlate
 [CA1711: Gli identificatori non devono contenere un suffisso non corretto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Vedere anche
 [Gli attributi](/dotnet/standard/design-guidelines/attributes) [gestione e generazione di eventi](/dotnet/standard/events/index)