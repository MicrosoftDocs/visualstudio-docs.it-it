---
title: 'CA2141: i metodi Transparent non devono soddisfare i LinkDemand | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 938bda4d4b5c96b9627cf11aae81c51d269c0e5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:I metodi Transparent non devono soddisfare i LinkDemand
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo SecurityTransparent chiama un metodo in un assembly che non è contrassegnato con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attributo (APTCA) o un metodo SecurityTransparent soddisfa un <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` per un tipo o un metodo.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Soddisfare un LinkDemand è un'operazione sensibile di sicurezza che può causare l'elevazione non intenzionale dei privilegi. Il codice SecurityTransparent non deve soddisfare i LinkDemand, perché non è soggetta agli stessi requisiti di controllo di sicurezza del codice SecurityCritical. I metodi Transparent negli assembly di livello 1 set di regole di sicurezza causerà tutti i LinkDemand soddisfano da convertire in richieste complete in fase di esecuzione, questo può causare problemi di prestazioni. Nell'assembly di livello 2 set di regole di sicurezza, i metodi transparent non riuscirà per la compilazione del compilatore just-in-time (JIT), se si tenta di soddisfare un LinkDemand.  
  
 Negli assembly che utilizzano la sicurezza di livello 2, i tentativi da parte di un metodo SecurityTransparent di soddisfare un LinkDemand o chiamare un metodo in un assembly non APTCA genera un <xref:System.MethodAccessException>; negli assembly di livello 1 LinkDemand diventa una richiesta completa.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, contrassegnare il metodo di accesso con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo o rimuovere il LinkDemand dal metodo di accesso.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 In questo esempio, un metodo trasparente tenta di chiamare un metodo che presenta un LinkDemand. Questa regola funzionerà su questo codice.  
  
 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]