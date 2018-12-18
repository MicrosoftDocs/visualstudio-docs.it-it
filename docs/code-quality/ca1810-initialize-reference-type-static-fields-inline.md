---
title: 'CA1810: Inizializzare i campi statici del tipo di riferimento inline'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0751a4f8f4402d6ba9a3128601ad6e735ac0d3e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inizializzare i campi statici del tipo di riferimento inline
|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo di riferimento dichiara un costruttore statico esplicito.

## <a name="rule-description"></a>Descrizione della regola
 Quando un tipo dichiara un costruttore statico esplicito, tramite il compilatore JIT (Just-In-Time) viene aggiunto un controllo a ogni metodo statico del tipo e a ogni costruttore di istanza del tipo per assicurare che il costruttore statico sia stato precedentemente chiamato. L'inizializzazione statica viene attivato quando si accede a qualsiasi membro statico o quando viene creata un'istanza del tipo. Tuttavia, l'inizializzazione statica non viene generato se si dichiara una variabile del tipo, ma non utilizzarlo, che può essere importante se l'inizializzazione viene modificato lo stato globale.

 Quando tutti i dati statici vengono inizializzati inline e non è dichiarato un costruttore statico esplicito, i compilatori Microsoft intermediate language (MSIL) aggiungono il `beforefieldinit` flag e un costruttore statico, che inizializza i dati statici, per il tipo di codice MSIL definizione. Quando il compilatore JIT rileva il `beforefieldinit` flag, la maggior parte dei casi non vengono aggiunti i controlli dei costruttori statici. L'inizializzazione statica è garantito che si verifichi in un momento prima tutti i campi statici sono accessibili, ma non prima che venga richiamato un costruttore di istanza o metodo statico. Si noti che l'inizializzazione statica può verificarsi in qualsiasi momento dopo la dichiarazione di una variabile del tipo.

 I controlli dei costruttori statici possono ridurre le prestazioni. Spesso un costruttore statico viene utilizzato solo per inizializzare i campi statici, in cui è necessario solo assicurarsi che l'inizializzazione statica caso si verifica prima del primo accesso di un campo statico. Il `beforefieldinit` comportamento è appropriato per questi e molti altri tipi. È solo quando l'inizializzazione statica influisce sullo stato globale e viene soddisfatta una delle operazioni seguenti:

-   L'effetto sullo stato globale è dispendioso e non è obbligatorio se non viene utilizzato il tipo.

-   Gli effetti di stato globale è possibile accedere senza l'accesso a tutti i campi statici del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando vengono dichiarati e rimuovere il costruttore statico.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È consigliabile escludere un avviso da questa regola se le prestazioni non rappresentano un problema. o se le modifiche di stato globale causati dall'inizializzazione statica sono dispendiose o devono essere garantita per verificarsi prima che viene chiamato un metodo statico del tipo o viene creata un'istanza del tipo.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `StaticConstructor`, che viola la regola e un tipo, `NoStaticConstructor`, che sostituisce il costruttore statico con l'inizializzazione inline per soddisfare la regola.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

 Si noti l'aggiunta del `beforefieldinit` flag nella definizione di codice MSIL per il `NoStaticConstructor` classe.

 **public class auto ansi StaticConstructor** **estende [mscorlib**
**{**
**} / / fine della classe StaticConstructor** 
 **Class auto pubblica ansi beforefieldinit NoStaticConstructor** **estende [mscorlib**
**{** 
 **} / / fine della classe NoStaticConstructor**
## <a name="related-rules"></a>Regole correlate
 [CA2207: Inizializzare i campi statici dei tipi di valore inline](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)