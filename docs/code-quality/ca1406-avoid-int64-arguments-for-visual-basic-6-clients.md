---
title: 'CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6 | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ed47a2ccea76ce9cb6e2a1ef6dd73d53c961544c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6
|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|Category|Microsoft.Interoperability|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un membro viene dichiarato un tipo contrassegnato specificatamente come visibile al modello COM (Component Object) che accetta un <xref:System.Int64?displayProperty=fullName> argomento.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I client COM Visual Basic 6 non è possibile accedere interi a 64 bit.  
  
 Per impostazione predefinita, sono visibili a COM seguente: assembly, i tipi pubblici, i membri di istanza pubblici nei tipi pubblici e tutti i membri dei tipi di valore pubblico. Tuttavia, per ridurre i falsi positivi, la regola richiede la visibilità COM di tipo per indicare in modo esplicito; l'assembly che contiene deve essere contrassegnato con il <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> impostato su `false` e il tipo deve essere contrassegnato con il <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `true`.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola per un parametro il cui valore può sempre essere espresso come integrale a 32 bit, modificare il tipo di parametro in <xref:System.Int32?displayProperty=fullName>. Se il valore del parametro può essere maggiore di quanto può essere espresso come un integrale a 32 bit, modificare il tipo di parametro in <xref:System.Decimal?displayProperty=fullName>. Si noti che entrambi <xref:System.Single?displayProperty=fullName> e <xref:System.Double?displayProperty=fullName> perdita di precisione in corrispondenza degli intervalli di superiori di <xref:System.Int64> tipo di dati. Se il membro non deve essere visibile a COM, contrassegnarlo con il <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `false`.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se si è certi che i client COM Visual Basic 6 non accederanno al tipo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola la regola.  
  
 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)   
 [Tipo di dati Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)