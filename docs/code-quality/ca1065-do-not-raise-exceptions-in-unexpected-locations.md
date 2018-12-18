---
title: 'CA1065: Non generare eccezioni in posizioni non previste'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 477286e437a901d15dd7a13a6bc1d9f7634b3b73
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Non generare eccezioni in posizioni non previste

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Category|Microsoft.Design|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un metodo che normalmente non genera eccezioni genera un'eccezione.

## <a name="rule-description"></a>Descrizione della regola

Metodi che non devono generare eccezioni possono essere suddivisi in categorie come indicato di seguito:

- Metodi Get di proprietà

- Metodi della funzione di accesso agli eventi

- Metodi Equals

- Metodi GetHashCode

- Metodi ToString

- Costruttori statici

- Finalizzatori

- Eliminazione dei metodi

- Operatori di uguaglianza

- Operatori di Cast impliciti

Le sezioni seguenti illustrano questi tipi di metodo.

### <a name="property-get-methods"></a>Metodi Get di proprietà

Le proprietà sono fondamentalmente smart. Pertanto, devono comportarsi come un campo il più possibile. I campi non generano eccezioni e non dovrebbero proprietà. Se si dispone di una proprietà che genera un'eccezione, prendere in considerazione è un metodo.

Le eccezioni seguenti possono essere generate da un metodo get della proprietà:

- <xref:System.InvalidOperationException?displayProperty=fullName> tutti i derivati e (inclusi <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> e tutti i derivati

- <xref:System.ArgumentException?displayProperty=fullName> (solo da indicizzata get)

- <xref:System.Collections.Generic.KeyNotFoundException> (solo da indicizzata get)

### <a name="event-accessor-methods"></a>Metodi della funzione di accesso agli eventi

Funzioni di accesso eventi devono essere operazioni semplici che non generano eccezioni. Un evento non deve generare un'eccezione quando si tenta di aggiungere o rimuovere un gestore eventi.

Le eccezioni seguenti possono essere generate da una funzione di accesso eventi:

- <xref:System.InvalidOperationException?displayProperty=fullName> tutti i derivati e (inclusi <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> e tutti i derivati

- <xref:System.ArgumentException> e derivati

### <a name="equals-methods"></a>Metodi Equals

Nell'esempio **è uguale a** metodi non devono generare eccezioni:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- <xref:System.IEquatable%601.Equals%2A>

Un **è uguale a** metodo dovrebbe restituire `true` o `false` anziché generare un'eccezione. Ad esempio, se Equals vengono passati due tipi non corrispondenti deve restituire `false` anziché generare un <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Metodi GetHashCode

Nell'esempio **GetHashCode** metodi in genere non devono generare eccezioni:

- <xref:System.Object.GetHashCode%2A>

- <xref:System.Collections.IEqualityComparer.GetHashCode%2A>

**GetHashCode** deve sempre restituire un valore. In caso contrario, è possibile perdere elementi nella tabella hash.

Le versioni di **GetHashCode** che accettano un argomento può generare un <xref:System.ArgumentException>. Tuttavia, **Object. GetHashCode** non deve mai generare un'eccezione.

### <a name="tostring-methods"></a>Metodi ToString

Il debugger utilizza <xref:System.Object.ToString%2A?displayProperty=fullName> per consentire di visualizzare informazioni sugli oggetti in formato stringa. Pertanto, **ToString** non dovrebbero modificare lo stato di un oggetto e non non deve generare eccezioni.

### <a name="static-constructors"></a>Costruttori statici

Il tipo sarà inutilizzabile nel dominio applicazione corrente a causa la generazione di eccezioni da un costruttore statico. È un buon motivo (ad esempio un problema di sicurezza) per generare un'eccezione da un costruttore statico.

### <a name="finalizers"></a>Finalizzatori

Generare un'eccezione da un finalizzatore il CLR esito negativo rapido, che a sua volta il processo. Pertanto, la generazione di eccezioni in un finalizzatore deve essere sempre evitata.

### <a name="dispose-methods"></a>Eliminazione dei metodi

Oggetto <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metodo non deve generare un'eccezione. Dispose viene spesso chiamato come parte della logica di pulizia in un `finally` clausola. Pertanto, in modo esplicito la generazione di un'eccezione da Dispose forza l'utente dovrà aggiungere la gestione delle eccezioni di `finally` clausola.

Il **Dispose (false)** percorso del codice non deve mai generare eccezioni, poiché Dispose viene quasi sempre chiamato da un finalizzatore.

### <a name="equality-operators--"></a>Gli operatori di uguaglianza (= =,! =)

Come i metodi Equals, gli operatori di uguaglianza devono restituire `true` o `false`e non devono generare eccezioni.

### <a name="implicit-cast-operators"></a>Operatori di Cast impliciti

Poiché l'utente è spesso a conoscenza che è stato chiamato un operatore di cast impliciti, un'eccezione generata dall'operatore di cast implicito è imprevista. Pertanto, eccezioni non devono essere generate dagli operatori di cast impliciti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per le funzioni Get di proprietà, di modificare la logica in modo che non sia più associata a un'eccezione o modificare la proprietà in un metodo.

Per tutti gli altri tipi di metodo elencate in precedenza, è possibile modificare la logica in modo che non è più necessario generare un'eccezione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi

Se la violazione è stata causata da una dichiarazione di eccezione anziché un'eccezione generata, è possibile eliminare un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate

- [CA2219: Non generare eccezioni in clausole di eccezione](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Vedere anche

- [Avvisi di progettazione](../code-quality/design-warnings.md)