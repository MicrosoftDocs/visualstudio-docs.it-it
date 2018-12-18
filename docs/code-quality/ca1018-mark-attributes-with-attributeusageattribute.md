---
title: 'CA1018: Contrassegnare gli attributi con AttributeUsageAttribute'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7949477e7fec9e215fd84eaa15d937be969fa102
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Contrassegnare gli attributi con AttributeUsageAttribute
|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il <xref:System.AttributeUsageAttribute?displayProperty=fullName> attributo non è presente sull'attributo personalizzato.

## <a name="rule-description"></a>Descrizione della regola
 Quando si definisce un attributo personalizzato, contrassegnarlo tramite <xref:System.AttributeUsageAttribute> per indicare la posizione nel codice sorgente può essere applicato l'attributo personalizzato. Il significato e l'utilizzo previsto di un attributo ne determinano le posizioni valide nel codice. Ad esempio, è possibile definire un attributo che identifica la persona responsabile per la gestione e l'ottimizzazione di ogni tipo in una raccolta, e responsabilità viene sempre assegnata a livello di tipo. In questo caso, i compilatori devono abilitare l'attributo su classi, enumerazioni e le interfacce, ma non devono abilitarla nei metodi, eventi o proprietà. Procedure e i criteri organizzativi indicano se l'attributo deve essere abilitato per gli assembly.

 Il <xref:System.AttributeTargets?displayProperty=fullName> enumerazione definisce le destinazioni che è possibile specificare un attributo personalizzato. Se si omette <xref:System.AttributeUsageAttribute>, l'attributo personalizzato sarà valida per tutte le destinazioni, come definito dal `All` valore <xref:System.AttributeTargets> enumerazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, specificare le destinazioni per l'attributo utilizzando <xref:System.AttributeUsageAttribute>. Vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È necessario correggere una violazione di questa regola anziché escludere il messaggio. Anche se l'attributo eredita <xref:System.AttributeUsageAttribute>, l'attributo deve essere presenta per semplificare la manutenzione del codice.

## <a name="example"></a>Esempio
 L'esempio seguente definisce due attributi. `BadCodeMaintainerAttribute` in modo non corretto omette il <xref:System.AttributeUsageAttribute> istruzione, e `GoodCodeMaintainerAttribute` implementa correttamente l'attributo descritto in precedenza in questa sezione. Si noti che la proprietà `DeveloperName` è richiesta dalla regola di progettazione [CA1019: definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) e viene inclusa per completezza.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Evitare attributi non sealed](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vedere anche
 [Attributi](/dotnet/standard/design-guidelines/attributes)