---
title: 'CA1303: Non passare valori letterali come parametri localizzati'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b621306bab673172c1c437ca0a959e4bc36f6da
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Non passare valori letterali come parametri localizzati
|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Category|Microsoft.Globalization|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo passa una stringa letterale come parametro a un costruttore o un metodo di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] libreria di classi e questa stringa deve essere localizzabile.

 Questo avviso viene generato quando una valore letterale stringa viene passata come valore per un parametro o una proprietà e uno o più delle seguenti condizioni sono true:

-   Il <xref:System.ComponentModel.LocalizableAttribute> attributo di parametro o la proprietà è impostata su true.

-   Il nome di parametro o la proprietà contiene "Text", "Messaggio" o "Didascalia".

-   Il nome del parametro di stringa che viene passato a un metodo Write o console. WriteLine è "value" o "format".

## <a name="rule-description"></a>Descrizione della regola
 Valori letterali stringa incorporati nel codice sorgente sono difficili da localizzare.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire il valore letterale stringa con una stringa recuperata tramite un'istanza di <xref:System.Resources.ResourceManager> classe.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se la libreria di codice non verrà localizzata o se la stringa non viene esposto all'utente finale o gli sviluppatori che utilizzano la libreria di codice.

 Gli utenti possono eliminare le segnalazioni sui metodi non da passare stringhe localizzate rinominando il parametro o una proprietà denominata o contrassegnando questi elementi come condizionali.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che genera un'eccezione se uno di due argomenti non è compreso nell'intervallo. Per il primo argomento, il costruttore di eccezione viene passato una valore letterale stringa, che violano questa regola. Per il secondo argomento, il costruttore è passato correttamente recuperata tramite una stringa di un <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Vedere anche
 [Risorse nelle applicazioni desktop](/dotnet/framework/resources/index)