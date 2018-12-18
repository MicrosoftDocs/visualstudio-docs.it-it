---
title: 'CA2143: I metodi Transparent non devono utilizzare SecurityDemand | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 073ce1d22662b46a19bf5cf36305df63500347a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: I metodi Transparent non devono utilizzare SecurityDemand
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Metodo o il tipo Trasparent è contrassegnato in modo dichiarativo con un <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` richiesta o il metodo chiama il <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> metodo.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Il codice trasparente per la sicurezza deve utilizzare richieste complete per prendere decisioni relative alla sicurezza e il codice critico per la sicurezza non deve basarsi sul codice trasparente per l'esecuzione della richiesta completa. Qualsiasi codice che esegue controlli di sicurezza, ad esempio SecurityDemand, deve essere invece SafeCritical.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 In generale, per correggere una violazione di questa regola, contrassegnare il metodo con il <xref:System.Security.SecuritySafeCriticalAttribute> attributo. È inoltre possibile rimuovere la richiesta.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 I file delle regole nel codice riportato di seguito perché un metodo trasparente esegue una richiesta di sicurezza dichiarativa.  
  
 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [CA2142: Il codice Transparent non deve essere protetto con LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)