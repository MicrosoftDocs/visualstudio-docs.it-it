---
title: 'CA2116: I metodi APTCA devono chiamare solo metodi APTCA'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70affcf0b71e9d0ae7440141f45f5ae0f2c04bf6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917619"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: I metodi APTCA devono chiamare solo metodi APTCA
|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo in un assembly con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attributo chiama un metodo in un assembly che non dispone dell'attributo.

## <a name="rule-description"></a>Descrizione della regola
 Per impostazione predefinita, i metodi pubblici o protetti in assembly con nomi sicuri sono protetti in modo implicito da un [le richieste di collegamento](/dotnet/framework/misc/link-demands) per l'attendibilità totale; solo completamente attendibili i chiamanti possono accedere a un assembly con nome sicuro. Gli assembly con nome sicuro contrassegnati con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attributo (APTCA) non dispone di questo tipo di protezione. L'attributo disabilita la richiesta di collegamento, rendendo l'assembly accessibile ai chiamanti che non dispongono di attendibilità totale, ad esempio di codice in esecuzione da una rete intranet o Internet.

 Quando l'attributo APTCA è presente in un assembly completamente attendibile e l'assembly esegue codice in un altro assembly che non consente chiamanti parzialmente attendibili, è possibile una violazione della sicurezza. Se due metodi `M1` e `M2` soddisfano le condizioni seguenti, i chiamanti malintenzionati possono utilizzare il metodo `M1` per ignorare la richiesta di collegamento di attendibilità totale implicita che protegge `M2`:

-   `M1` è un metodo pubblico dichiarato in un assembly completamente attendibile con l'attributo APTCA.

-   `M1` chiama un metodo `M2` all'esterno `M1`dell'assembly.

-   `M2`dell'assembly non ha l'attributo APTCA e, pertanto non deve essere eseguito da o per conto di chiamanti parzialmente attendibili.

 Un chiamante parzialmente attendibile `X` può chiamare metodo `M1`, provocando `M1` chiamare `M2`. Poiché `M2` non hanno l'attributo APTCA, il relativo chiamante immediato (`M1`) deve soddisfare una richiesta di collegamento per l'attendibilità totale; `M1` sia totalmente attendibile e pertanto soddisfa questo controllo. Il rischio di sicurezza è perché `X` contribuisce a soddisfare la richiesta di collegamento che consente di proteggere `M2` da chiamanti non attendibili. Di conseguenza, i metodi con l'attributo APTCA non devono chiamare metodi che non dispone dell'attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se l'attributo APCTA è necessaria, utilizzare una richiesta per proteggere il metodo che chiama l'assembly con attendibilità totale. Le autorizzazioni esatte dipenderà è richiesta la funzionalità esposta dal metodo. Se possibile, proteggere il metodo con una richiesta per l'attendibilità totale garantire che la funzionalità sottostante non è esposta a chiamanti parzialmente attendibili. In caso contrario, selezionare un set di autorizzazioni che protegge in modo efficace le funzionalità esposte.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che la funzionalità esposta dal metodo non direttamente o indirettamente consente ai chiamanti di accedere a informazioni riservate, operazioni o risorse che possono essere utilizzate in modo distruttivo.

## <a name="example"></a>Esempio
 L'esempio seguente usa due assembly e un'applicazione di test per illustrare la vulnerabilità di sicurezza rilevata da questa regola. Il primo assembly non ha l'attributo APTCA e non devono essere accessibili a chiamanti parzialmente attendibili (rappresentato da `M2` nella spiegazione precedente).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example"></a>Esempio
 Il secondo assembly completamente attendibile e consente ai chiamanti parzialmente attendibili (rappresentato da `M1` nella spiegazione precedente).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example"></a>Esempio
 L'applicazione di test (rappresentato da `X` nella spiegazione precedente) è parzialmente attendibile.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

 Questo esempio produce il seguente output:

 **Richiesta di attendibilità completa: richiesta non riuscita. ** 
 **ClassRequiringFullTrust.DoWork è stato chiamato.**
## <a name="related-rules"></a>Regole correlate
 [CA2117: I tipi APTCA devono estendere solo tipi di base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Vedere anche
 [Linee guida di codice sicuro](/dotnet/standard/security/secure-coding-guidelines) [utilizzo parzialmente di librerie da codice attendibile](/dotnet/framework/misc/using-libraries-from-partially-trusted-code) [le richieste di collegamento](/dotnet/framework/misc/link-demands) [dati e modellazione](/dotnet/framework/data/index)