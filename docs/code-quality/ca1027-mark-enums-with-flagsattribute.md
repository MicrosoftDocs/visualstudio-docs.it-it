---
title: 'CA1027: Contrassegnare le enumerazioni con FlagsAttribute'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0660ea1f83360d56633573557e52f40f3751bef5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Contrassegnare le enumerazioni con FlagsAttribute
|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 I valori di un'enumerazione pubblica sono potenze di due o combinazioni di altri valori definiti nell'enumerazione, e <xref:System.FlagsAttribute?displayProperty=fullName> attributo non è presente. Per ridurre i falsi positivi, questa regola segnala una violazione per le enumerazioni con valori contigui.

## <a name="rule-description"></a>Descrizione della regola
 Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Applicare <xref:System.FlagsAttribute> a un'enumerazione quando le relative costanti denominate possono essere combinate. Si consideri, ad esempio, un'enumerazione dei giorni della settimana in un'applicazione che tiene traccia di quali risorse del giorno sono disponibili. Se la disponibilità di ogni risorsa è codificata tramite l'enumerazione con <xref:System.FlagsAttribute> presente, qualsiasi combinazione di giorni può essere rappresentato. Senza l'attributo, è possibile rappresentare un solo giorno della settimana.

 Per i campi che vengono archiviate enumerazioni combinabili, i singoli valori di enumerazione vengono trattati come gruppi di bit nel campo. Pertanto, tali campi sono dette *campi di bit*. Per combinare i valori di enumerazione per l'archiviazione in un campo di bit, utilizzare gli operatori booleani condizionali. Per testare un campo di bit per determinare se è presente un valore di enumerazione specifico, utilizzare gli operatori logici Boolean. Per un campo di bit archiviare e recuperare correttamente i valori di enumerazione, ogni valore definito nell'enumerazione deve essere una potenza di due. In caso contrario, gli operatori logici Boolean non sarà in grado di estrarre i singoli valori di enumerazione che vengono archiviati nel campo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere <xref:System.FlagsAttribute> all'enumerazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola se non si desidera valori di enumerazione siano combinabili.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `DaysEnumNeedsFlags` è un'enumerazione che soddisfi i requisiti per l'utilizzo di <xref:System.FlagsAttribute>, ma non è presente. Il `ColorEnumShouldNotHaveFlag` enumerazione non dispongono di valori che sono potenze di due, ma specifica erroneamente <xref:System.FlagsAttribute>. Questa condizione viola regola [CA2217: non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.FlagsAttribute?displayProperty=fullName>