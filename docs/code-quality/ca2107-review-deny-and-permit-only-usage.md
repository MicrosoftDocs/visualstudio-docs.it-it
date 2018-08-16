---
title: "CA2107: Controllare l'utilizzo di Deny e PermitOnly"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d777379cdf5dc5d6be36989f95aadd80ca757e69
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915682"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Controllare l'utilizzo di Deny e PermitOnly
|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo contiene un controllo di sicurezza che specifica l'azione di sicurezza PermitOnly o Deny.

## <a name="rule-description"></a>Descrizione della regola
 Il <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> azione di sicurezza deve essere utilizzato solo da utenti che possiedono una conoscenza approfondita di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sicurezza. Il codice che usa queste azioni di sicurezza deve essere sottoposto a una revisione della sicurezza.

 Nega modifica il comportamento predefinito dell'analisi dello stack che si verifica in risposta a una richiesta di sicurezza. Consente di specificare le autorizzazioni che non devono essere concesse per la durata del metodo Deny, indipendentemente dalle autorizzazioni effettive dei chiamanti nello stack di chiamate. Se il percorso stack viene rilevato un metodo protetto da Deny e l'autorizzazione richiesta è inclusa nelle autorizzazioni negate, il percorso stack avrà esito negativo. Anche PermitOnly altera il comportamento predefinito dell'analisi dello stack. Consente al codice specificare solo le autorizzazioni che possono essere concesse, indipendentemente dalle autorizzazioni dei chiamanti. Se il percorso stack viene rilevato un metodo protetto da PermitOnly e l'autorizzazione richiesta non è incluso nelle autorizzazioni specificate da PermitOnly, il percorso stack avrà esito negativo.

 Codice che si basa su queste azioni deve essere valutato attentamente per le vulnerabilità di sicurezza a causa della limitata utilità e un comportamento complesso. Si consideri quanto segue.

-   [Le richieste di collegamento](/dotnet/framework/misc/link-demands) non sono interessati da Deny o PermitOnly.

-   Se Deny o PermitOnly si verifica lo stesso stack frame della richiesta che causa il percorso stack, le azioni di sicurezza non hanno effetto.

-   I valori utilizzati per costruire le autorizzazioni basate sul percorso in genere possono essere specificati in più modi. Negazione dell'accesso a un formato del percorso non negare l'accesso a tutti i moduli. Se, ad esempio, una condivisione file \\\Server\Share viene eseguito il mapping all'unità x:, per negare l'accesso a un file nella condivisione di rete è necessario negare \\\Server\Share\File, X:\File e ogni altro percorso che accede al file.

-   Un <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> possibile terminare un percorso stack prima che venga raggiunto Deny o PermitOnly.

-   Se un'istruzione Deny abbia effetto, in particolare, quando un chiamante dispone di un'autorizzazione che è bloccata da Deny, il chiamante può accedere direttamente alla risorsa protetta ignorando Deny. Analogamente, se il chiamante non dispone dell'autorizzazione negata, il percorso stack avrà esito negativo senza l'istruzione Deny.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Qualsiasi uso di queste azioni di sicurezza comporta una violazione. Per correggere una violazione, non utilizzare queste azioni di sicurezza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola solo dopo aver completato una revisione della sicurezza.

## <a name="example"></a>Esempio
 L'esempio seguente illustra alcune limitazioni di Deny.

 La libreria seguente contiene una classe che dispone di due metodi identici tranne che per le richieste di sicurezza che li proteggono.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example"></a>Esempio
 L'applicazione seguente illustra gli effetti di Deny sui metodi protetti dalla libreria.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

 Questo esempio produce il seguente output:

 **Domanda: Deny del chiamante non ha effetto su richiesta con autorizzazione oggetto dell'asserzione. ** 
 **LinkDemand: Deny del chiamante non ha alcun effetto su LinkDemand con autorizzazione oggetto dell'asserzione.** 
 **LinkDemand: Deny del chiamante non ha alcun effetto con il codice protetto LinkDemand.** 
 **LinkDemand: negare questa non ha alcun effetto con il codice protetto LinkDemand.**
## <a name="see-also"></a>Vedere anche
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName> [Linee guida di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)

