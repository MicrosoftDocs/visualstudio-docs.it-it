---
title: 'CA1304: Specificare CultureInfo'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dec38172f65b7b4d828dc96f0b2f51b28ce1ebd6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Specificare CultureInfo
|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo o costruttore chiama un membro che presenta un overload che accetta un <xref:System.Globalization.CultureInfo?displayProperty=fullName> parametro e il metodo o costruttore non chiama l'overload che accetta il <xref:System.Globalization.CultureInfo> parametro. Questa regola ignora le chiamate ai metodi seguenti:

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Descrizione della regola
 Quando un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider?displayProperty=fullName> oggetto non viene specificato, il valore predefinito fornito dal membro di overload potrebbe non produrre l'effetto desiderato in tutte le impostazioni locali. Inoltre, [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] membri scelgono impostazioni cultura predefinite e formattazione basata su ipotesi che potrebbero non essere corrette per il codice. Per garantire che il codice funzioni come previsto negli scenari, è necessario fornire informazioni specifiche delle impostazioni cultura in base alle linee guida seguenti:

-   Se il valore verrà visualizzato all'utente, utilizzare le impostazioni cultura correnti. Vedere <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

-   Se il valore verrà archiviato e accessibile da parte di software, vale a dire, mantenuto in un file o di un database, utilizzare le impostazioni cultura invarianti. Vedere <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

-   Se non si conosce la destinazione del valore, sono consumer di dati o provider di specificare le impostazioni cultura.

 Si noti che <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> viene utilizzato solo per recuperare le risorse localizzate con un'istanza di <xref:System.Resources.ResourceManager?displayProperty=fullName> classe.

 Anche se il comportamento predefinito del membro di overload è adatto alle proprie esigenze, è preferibile chiamare in modo esplicito l'overload specifico delle impostazioni cultura in modo che il codice autodocumentato e gestita in modo più semplice.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, utilizzare l'overload che accetta un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> e specificare l'argomento in base alle indicazioni elencate in precedenza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si è certi che il provider di formato delle impostazioni cultura predefinito è la scelta corretta e la gestibilità del codice non è una priorità di sviluppo importanti.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `BadMethod` causa due violazioni di questa regola. `GoodMethod` corregge la prima violazione passando le impostazioni cultura invarianti a System.String.Compare e corregge la seconda violazione passando le impostazioni cultura correnti per <xref:System.String.ToLower%2A> perché `string3` viene visualizzato all'utente.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato l'effetto delle impostazioni cultura correnti predefinito <xref:System.IFormatProvider> che è selezionata per il <xref:System.DateTime> tipo.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

 Questo esempio produce il seguente output:

 **6/4/1900 12:15:12 PM**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Regole correlate
 [CA1305: Specificare IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Vedere anche
[Utilizzo della classe CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)