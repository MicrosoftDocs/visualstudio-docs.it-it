---
title: 'CA1305: Specificare IFormatProvider'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 73ac9fe384088d509d7eee800b066571f995dd24
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Specificare IFormatProvider
|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo o costruttore chiama uno o più membri con overload che accettano un <xref:System.IFormatProvider?displayProperty=fullName> parametro e il metodo o costruttore non chiama l'overload che accetta il <xref:System.IFormatProvider> parametro. Questa regola ignora le chiamate a [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] metodi documentati come ignorando il <xref:System.IFormatProvider> parametro e inoltre i metodi seguenti:

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Descrizione della regola
 Quando un <xref:System.Globalization.CultureInfo?displayProperty=fullName> o <xref:System.IFormatProvider> oggetto non viene specificato, il valore predefinito fornito dal membro di overload potrebbe non produrre l'effetto desiderato in tutte le impostazioni locali. Inoltre, [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] membri scelgono impostazioni cultura predefinite e formattazione basata su ipotesi che potrebbero non essere corrette per il codice. Per assicurarsi che il codice funzioni come previsto per gli scenari, è necessario fornire informazioni specifiche delle impostazioni cultura in base alle linee guida seguenti:

-   Se il valore verrà visualizzato all'utente, utilizzare le impostazioni cultura correnti. Vedere <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

-   Se il valore verrà archiviato e a cui accede software (persistente in un file o database), utilizzare le impostazioni cultura invarianti. Vedere <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

-   Se non si conosce la destinazione del valore, sono consumer di dati o provider di specificare le impostazioni cultura.

 Si noti che <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> viene utilizzato solo per recuperare le risorse localizzate con un'istanza di <xref:System.Resources.ResourceManager?displayProperty=fullName> classe.

 Anche se il comportamento predefinito del membro di overload è adatto alle proprie esigenze, è preferibile chiamare in modo esplicito l'overload specifico delle impostazioni cultura in modo che il codice autodocumentato e gestita in modo più semplice.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, utilizzare l'overload che accetta un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> e specificare l'argomento in base alle indicazioni elencate in precedenza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si è certi che il provider di formato delle impostazioni cultura predefinito è la scelta corretta e in cui la gestibilità del codice non è una priorità di sviluppo importanti.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `BadMethod` causa due violazioni di questa regola. `GoodMethod` corregge la prima violazione passando le impostazioni cultura invarianti per <xref:System.String.Compare%2A>e corregge la seconda violazione passando le impostazioni cultura correnti a <xref:System.String.ToLower%2A> perché `string3` viene visualizzato all'utente.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato l'effetto delle impostazioni cultura correnti predefinito <xref:System.IFormatProvider> che è selezionata per il <xref:System.DateTime> tipo.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]

 Questo esempio produce il seguente output:

 **6/4/1900 12:15:12 PM**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Regole correlate
 [CA1304: Specificare CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Vedere anche
[Utilizzo della classe CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)