---
title: 'CA2106: Proteggere asserzioni | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 33e200b06ed9bb0999116ea91a64b06aaa879067
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2106-secure-asserts"></a>CA2106: Asserzioni protette
|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo asserisce un'autorizzazione e non vengono eseguiti controlli di sicurezza sul chiamante.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quando si asserisce un'autorizzazione di sicurezza senza eseguire alcun controllo di sicurezza, nel codice potrebbero restare punti deboli nella sicurezza. Un percorso stack di sicurezza si interrompe quando viene dichiarata un'autorizzazione di sicurezza. Se si asserisce un'autorizzazione senza eseguire alcun controllo sul chiamante, il chiamante indirettamente eseguire codice utilizzando le autorizzazioni. Asserzioni senza controlli di sicurezza sono consentite solo quando si è certi che l'asserzione non può essere utilizzato in modo dannoso. Un'asserzione è puramente informativo se il codice chiamato non provoca problemi o gli utenti non è possibile passare informazioni arbitrarie al codice chiamato.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere una richiesta di sicurezza per il metodo o il tipo dichiarante.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola solo dopo un'attenta revisione della sicurezza.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)