---
title: 'CA2147: I metodi Transparent non possono utilizzare sicurezza asserzioni | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 38ac5492c987515c7c6504c91d2e035f8b8645ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Il codice Transparent non può utilizzare asserzioni di sicurezza
|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Il codice contrassegnato come <xref:System.Security.SecurityTransparentAttribute> non vengono concesse autorizzazioni sufficienti per l'asserzione.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola analizza tutti i metodi e tipi in un assembly che entrambi 100% transparent o trasparente/critico e contrassegna l'utilizzo dichiarativo o imperativo di <xref:System.Security.CodeAccessPermission.Assert%2A>.  
  
 In fase di esecuzione delle chiamate a <xref:System.Security.CodeAccessPermission.Assert%2A> da codice transparent causerà un <xref:System.InvalidOperationException> generata. Ciò può verificarsi in due assembly trasparenti al 100% e anche in un assembly trasparente/critico misti in cui un metodo o tipo è dichiarato trasparente, ma include un dichiarativo o imperativo di Assert.  
  
 Il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 è stata introdotta una funzionalità denominata *trasparenza*. Tipi, campi, interfacce, classi e i singoli metodi possono essere trasparente o critico.  
  
 Il codice trasparente non è possibile elevare i privilegi di sicurezza. Pertanto, tutte le autorizzazioni concesse o richiesta viene automaticamente vengono passate tramite il codice per il dominio applicazione chiamante o host. Elevazioni esempi di istruzioni Assert, LinkDemands, SuppressUnmanagedCode e `unsafe` codice.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per risolvere il problema, contrassegnare il codice che chiama l'asserzione con il <xref:System.Security.SecurityCriticalAttribute>, o rimuovere l'asserzione.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un messaggio da questa regola.  
  
## <a name="example"></a>Esempio  
 Questo codice avrà esito negativo se `SecurityTestClass` è trasparente, quando il `Assert` metodo genera un <xref:System.InvalidOperationException>.  
  
 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]  
  
## <a name="example"></a>Esempio  
 Un'opzione consiste nel metodo SecurityTransparentMethod nell'esempio seguente la revisione del codice e se il metodo è considerato sicuro per l'elevazione dei privilegi, contrassegnarlo con critico ciò richiede che un dettagliato, completa e privo di errori di sicurezza controllo deve essere eseguito nel metodo insieme a qualsiasi callout che si verificano all'interno del metodo sotto l'asserzione:  
  
 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]  
  
 Un'altra opzione consiste nel rimuovere l'asserzione dal codice e lasciare qualsiasi file successivi dei / o autorizzazione richieste SecurityTransparentMethod al chiamante. In questo modo i controlli di sicurezza. In questo caso, nessun controllo di sicurezza in genere è necessario, perché le richieste di autorizzazione trasmetterà il chiamante e/o il dominio dell'applicazione. Le richieste di autorizzazione sono strettamente controllate mediante criteri di sicurezza, l'ambiente host e concede l'autorizzazione di codice sorgente.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di sicurezza](../code-quality/security-warnings.md)