---
title: 'CA2106: Asserzioni protette'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40d497efd766fa5716b92e16ad513df85a41d2cf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
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
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Linee guida di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)