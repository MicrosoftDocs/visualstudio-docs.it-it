---
title: 'CA2136: I membri non devono avere annotazioni di trasparenza in conflitto | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: aad39e8b42a709aabc6321718a671510a5b686da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: I membri non devono avere annotazioni di trasparenza in conflitto
|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|CheckId|CA2136|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Questa regola viene attivata quando un membro del tipo è contrassegnato con un <xref:System.Security> attributo di sicurezza che dispone di una trasparenza diversa rispetto all'attributo di sicurezza di un contenitore del membro.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Gli attributi di trasparenza vengono applicati da elementi di codice con un ambito più ampio a elementi con ambito più ridotto. Gli attributi di trasparenza di elementi di codice che presentano un ambito più ampio hanno la precedenza su quelli contenuti nel primo elemento. Ad esempio, una classe contrassegnata con il <xref:System.Security.SecurityCriticalAttribute> attributo non può contenere un metodo contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> attributo.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere questa violazione, rimuovere l'attributo di sicurezza dall'elemento di codice che ha un ambito inferiore oppure modificarne l'attributo corrispondente all'elemento di codice che lo contiene.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere gli avvisi da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, un metodo è contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> attributo e è un membro di una classe contrassegnata con il <xref:System.Security.SecurityCriticalAttribute> attributo. L'attributo di sicurezza sicuro deve essere rimosso.  
  
 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]