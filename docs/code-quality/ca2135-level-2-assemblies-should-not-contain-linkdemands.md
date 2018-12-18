---
title: 'CA2135: Gli assembly di livello 2 non devono contenere LinkDemands | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ea4d0adf3573410c9f8a25e6b5d3abf2615c8ad3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Gli assembly di livello 2 non devono contenere LinkDemands
|||  
|-|-|  
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2135|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Una classe o membro della classe sta utilizzando un <xref:System.Security.Permissions.SecurityAction> in un'applicazione che utilizza una sicurezza di livello 2.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I LinkDemand sono deprecati nel set di regole per la sicurezza di livello 2. Anziché utilizzare i LinkDemand per applicare la sicurezza in fase di compilazione just-in-time (JIT), contrassegnare i metodi, tipi e i campi con il <xref:System.Security.SecurityCriticalAttribute> attributo.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il <xref:System.Security.Permissions.SecurityAction> e contrassegnare il tipo o membro con il <xref:System.Security.SecurityCriticalAttribute> attributo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, il <xref:System.Security.Permissions.SecurityAction> devono essere rimossi e il metodo contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> attributo.  
  
 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]