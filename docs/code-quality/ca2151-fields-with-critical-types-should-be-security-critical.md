---
title: 'CA2151: I campi con tipi critici devono essere SecurityCritical | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 76a763e2adcf8af588d08a9cd443a4eaf6e36e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151: I campi con tipi critici devono essere SecurityCritical
|||  
|-|-|  
|TypeName||  
|CheckId|CA2151|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un campo trasparente per la sicurezza o un campo critico sicuro è dichiarato. Il tipo è specificato come critico per la sicurezza. Ad esempio:  
  
```csharp  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      Type1 m_field; // CA2151, transparent field of critical type  
   }  
  
```  
  
 In questo esempio, `m_field` è un campo trasparente per la sicurezza di un tipo che è critico per la sicurezza.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Per usare i tipi critici per la sicurezza, il codice che fa riferimento al tipo deve essere critico per la sicurezza critico per la sicurezza e richiamabile da codice trasparente. Questo vale anche se il riferimento è indiretto. Ad esempio, quando si fa riferimento a un campo trasparente che dispone di un tipo critico, il codice deve essere critico per la sicurezza o critico per la sicurezza e richiamabile da codice trasparente. Pertanto, un campo trasparente per la sicurezza o critico per la sicurezza e richiamabile da codice trasparente è fuorviante perché il codice trasparente non potrà comunque accedere al campo.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere la violazione di questa regola, contrassegnare il campo con l'attributo <xref:System.Security.SecurityCriticalAttribute> oppure rendere il tipo a cui il campo fa riferimento trasparente per la sicurezza o critico per la sicurezza e richiamabile da codice trasparente.  
  
```csharp  
// Fix 1: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
// Fix 2: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   class Type1 { } // Type1 is now transparent  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
```  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]  
  
### <a name="comments"></a>Commenti