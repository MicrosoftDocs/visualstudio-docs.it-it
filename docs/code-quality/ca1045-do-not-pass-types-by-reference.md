---
title: 'CA1045: Non passare tipi riferimento | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7542e21963f272dd10180203a52bee9994de2cdc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Non passare i tipi per riferimento
|||  
|-|-|  
|TypeName|DoNotPassTypesByReference|  
|CheckId|CA1045|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo pubblico o protetto in un tipo pubblico presenta un `ref` parametro che accetta un tipo primitivo, un tipo riferimento o un tipo di valore che non è uno dei tipi incorporati.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Passaggio di tipi per riferimento (mediante `out` o `ref`) richiede esperienza nell'utilizzo dei puntatori, conoscenza delle differenziano tra tipi di valore e tipi di riferimento e la gestione di metodi che presentano più valori restituiti. Inoltre, la differenza tra `out` e `ref` parametri non è sempre nota.  
  
 Quando un tipo di riferimento viene passato "riferimento", il metodo intenzione di utilizzare il parametro per restituire un'istanza diversa dell'oggetto. (Il passaggio di un tipo di riferimento per riferimento è noto anche come mediante un puntatore doppio, puntatore a un puntatore o un riferimento indiretto doppio.) Utilizzando il valore predefinito convenzione, il passaggio "per valore", un parametro che accetta un tipo di riferimento già riceve un puntatore all'oggetto. Il puntatore, non l'oggetto a cui fa riferimento, viene passato per valore. Il passaggio per valore indica che il metodo non è possibile modificare il puntatore affinché punti a una nuova istanza del riferimento a un tipo, ma è possibile modificare il contenuto dell'oggetto a cui fa riferimento. Per la maggior parte delle applicazioni ciò è sufficiente e produce il comportamento desiderato.  
  
 Se un metodo deve restituire un'istanza diversa, utilizzare il valore restituito del metodo per eseguire questa operazione. Vedere la <xref:System.String?displayProperty=fullName> classe per un'ampia gamma di metodi che operano su stringhe e restituisce una nuova istanza di una stringa. Tramite questo modello, questa viene lasciata al chiamante di decidere se l'oggetto originale verrà mantenuta.  
  
 Anche se i valori restituiti siano comuni e ampiamente utilizzati, l'applicazione corretta di `out` e `ref` parametri richiede progettazione intermedia competenze e codifica. Per un pubblico generico non possono prevedere gli utenti in grado di utilizzare con gli architetti di libreria `out` o `ref` parametri.  
  
> [!NOTE]
>  Quando si lavora con i parametri che sono strutture di grandi dimensioni, le risorse aggiuntive necessarie per copiare queste strutture potrebbero causare un effetto sulle prestazioni quando si passa per valore. In questi casi, è possibile utilizzare `ref` o `out` parametri.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola causata da un tipo di valore, il metodo con restituire l'oggetto come relativo valore restituito. Se il metodo deve restituire più valori, riprogettare per restituire una singola istanza di un oggetto che contiene i valori.  
  
 Per correggere una violazione di questa regola causata da un tipo riferimento, assicurarsi che il comportamento che si desidera sia per restituire una nuova istanza del riferimento. Questo caso, il metodo deve utilizzare il valore restituito per eseguire questa operazione.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È consigliabile escludere un avviso da questa regola. Tuttavia, questa progettazione potrebbe provocare problemi di usabilità.  
  
## <a name="example"></a>Esempio  
 La libreria seguente mostra le due implementazioni di una classe che genera le risposte per i commenti e suggerimenti dell'utente. La prima implementazione (`BadRefAndOut`) impone all'utente di libreria di gestire tre valori restituiti. L'implementazione del secondo (`RedesignedRefAndOut`) semplifica l'esperienza utente tramite la restituzione di un'istanza di una classe contenitore (`ReplyData`) che gestisce i dati come una singola unità.  
  
 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## <a name="example"></a>Esempio  
 L'applicazione riportata di seguito viene illustrata l'esperienza dell'utente. La chiamata alla libreria riprogettata (`UseTheSimplifiedClass` (metodo)) è più semplice, e può essere gestite facilmente le informazioni restituite dal metodo. L'output dei due metodi è identico.  
  
 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## <a name="example"></a>Esempio  
 La libreria di esempio seguente viene illustrato come `ref` vengono utilizzati i parametri per i tipi di riferimento e Mostra un modo migliore per implementare questa funzionalità.  
  
 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## <a name="example"></a>Esempio  
 La seguente applicazione chiama ogni metodo nella libreria per illustrare il comportamento.  
  
 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 Questo esempio produce il seguente output:  
  
 **Modifica del puntatore - passato per valore:**  
**12345**  
**12345**  
**Modifica del puntatore, passato per riferimento:**  
**12345**  
**ABCDE 12345**  
**Passaggio per valore restituito:**  
**ABCDE 12345**   
## <a name="related-rules"></a>Regole correlate  
 [CA1021: Evitare parametri out](../code-quality/ca1021-avoid-out-parameters.md)