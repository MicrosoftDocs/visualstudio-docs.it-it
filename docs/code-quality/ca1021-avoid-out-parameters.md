---
title: 'CA1021: Evitare parametri out'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86503ae5abb994b5b1d687744371a57ff6086e43
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Evitare parametri out
|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto in un tipo pubblico presenta un `out` parametro.

## <a name="rule-description"></a>Descrizione della regola
 Passaggio di tipi per riferimento (mediante `out` o `ref`) richiede esperienza nell'utilizzo dei puntatori, conoscenza delle differenziano tra tipi di valore e tipi di riferimento e dei metodi con più valori restituiti. Inoltre, la differenza tra `out` e `ref` parametri non è sempre nota.

 Quando un tipo di riferimento viene passato "riferimento", il metodo intenzione di utilizzare il parametro per restituire un'istanza diversa dell'oggetto. Il passaggio di un tipo di riferimento per riferimento è noto anche come mediante un puntatore doppio, puntatore a un puntatore o un riferimento indiretto doppio. Utilizzando la convenzione, il passaggio "per valore", un parametro che accetta un tipo di riferimento già riceve un puntatore all'oggetto. Il puntatore, non l'oggetto a cui fa riferimento, viene passato per valore. Passaggio per valore significa che il metodo non è possibile modificare il puntatore affinché punti a una nuova istanza del tipo di riferimento. Tuttavia, è possibile modificare il contenuto dell'oggetto a cui fa riferimento. Per la maggior parte delle applicazioni ciò è sufficiente e produce il comportamento desiderato.

 Se un metodo deve restituire un'istanza diversa, utilizzare il valore restituito del metodo per eseguire questa operazione. Vedere la <xref:System.String?displayProperty=fullName> classe per un'ampia gamma di metodi che operano su stringhe e restituisce una nuova istanza di una stringa. Quando si utilizza questo modello, il chiamante deve decidere se l'oggetto originale verrà mantenuta.

 Anche se i valori restituiti siano comuni e ampiamente utilizzati, l'applicazione corretta di `out` e `ref` parametri richiede progettazione intermedia competenze e codifica. Per un pubblico generico non possono prevedere gli utenti in grado di utilizzare con gli architetti di libreria `out` o `ref` parametri.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola causata da un tipo di valore, il metodo con restituire l'oggetto come relativo valore restituito. Se il metodo deve restituire più valori, riprogettare per restituire una singola istanza di un oggetto che contiene i valori.

 Per correggere una violazione di questa regola causata da un tipo riferimento, assicurarsi che il comportamento desiderato sia per restituire una nuova istanza del riferimento. Questo caso, il metodo deve utilizzare il valore restituito per eseguire questa operazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola. Tuttavia, questa progettazione potrebbe provocare problemi di usabilità.

## <a name="example"></a>Esempio
 La libreria seguente mostra le due implementazioni di una classe che genera le risposte per i commenti e suggerimenti dell'utente. La prima implementazione (`BadRefAndOut`) impone all'utente di libreria di gestire tre valori restituiti. L'implementazione del secondo (`RedesignedRefAndOut`) semplifica l'esperienza utente tramite la restituzione di un'istanza di una classe contenitore (`ReplyData`) che gestisce i dati come una singola unità.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Esempio
 L'applicazione riportata di seguito viene illustrata l'esperienza dell'utente. La chiamata alla libreria riprogettata (`UseTheSimplifiedClass` (metodo)) è più semplice, e può essere gestite facilmente le informazioni restituite dal metodo. L'output dei due metodi è identico.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Esempio
 La libreria di esempio seguente viene illustrato come `ref` parametri per i tipi di riferimento vengono utilizzati e Mostra un modo migliore per implementare questa funzionalità.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Esempio
 La seguente applicazione chiama ogni metodo nella libreria per illustrare il comportamento.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

 Questo esempio produce il seguente output:

 **Puntatore Changing - passati per valore:**
**12345**
**12345**
**puntatore Changing - passati per riferimento:** 
 ** 12345**
**ABCDE 12345**
**passaggio per valore restituito:**
**ABCDE 12345**
## <a name="try-pattern-methods"></a>Provare i metodi del pattern

### <a name="description"></a>Descrizione
 I metodi che implementano il **provare\<qualcosa >** modello, ad esempio <xref:System.Int32.TryParse%2A?displayProperty=fullName>, non generano questa violazione. Nell'esempio seguente viene illustrata una struttura (tipo di valore) che implementa il <xref:System.Int32.TryParse%2A?displayProperty=fullName> metodo.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1045: Non passare i tipi per riferimento](../code-quality/ca1045-do-not-pass-types-by-reference.md)