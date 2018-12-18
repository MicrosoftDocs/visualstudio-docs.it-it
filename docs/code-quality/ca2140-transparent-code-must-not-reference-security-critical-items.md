---
title: 'CA2140: Il codice Transparent non deve fare riferimento elementi SecurityCritical | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0970bd3a05975707cbbac3f79dbece234adb16ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Il codice Transparent non deve far riferimento a elementi SecurityCritical
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo trasparente:  
  
-   gestisce un tipo di eccezione di sicurezza critico per la protezione  
  
-   ha un parametro che è contrassegnato come un tipo SecurityCritical  
  
-   contiene un parametro generico con vincoli SecurityCritical  
  
-   dispone di una variabile locale di un tipo SecurityCritical  
  
-   fa riferimento a un tipo contrassegnato come SecurityCritical  
  
-   chiama un metodo contrassegnato come sicurezza critico  
  
-   riferimento a un campo contrassegnato come sicurezza critico  
  
-   Restituisce un tipo che è contrassegnato come sicurezza critico  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un elemento di codice che è contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> attributo è critico per la sicurezza. Un metodo trasparente non può usare un elemento critico per la sicurezza. Se un tipo trasparente tenta di usare un tipo SecurityCritical un <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , o <xref:System.FieldAccessException> viene generato.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, eseguire una delle operazioni seguenti:  
  
-   Contrassegnare l'elemento di codice che utilizza il codice SecurityCritical con il <xref:System.Security.SecurityCriticalAttribute> attributo  
  
     \- oppure -  
  
-   Rimuovere il <xref:System.Security.SecurityCriticalAttribute> attributo dagli elementi di codice che sono contrassegnati come SecurityCritical e invece contrassegnarli con il <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityTransparentAttribute> attributo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Negli esempi seguenti, un metodo trasparente tenta di fare riferimento a una raccolta generica, un campo e un metodo SecurityCritical.  
  
 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>