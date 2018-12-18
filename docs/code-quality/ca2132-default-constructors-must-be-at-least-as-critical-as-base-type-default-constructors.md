---
title: 'CA2132: I costruttori predefiniti devono essere critici almeno come i costruttori predefiniti del tipo di base | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 752103825a25c4352ccc21730b8d2b7265f8f41b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base
|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
> [!NOTE]
>  Questo avviso viene applicato solo al codice che esegue CoreCLR (la versione di CLR è specifico di applicazioni Silverlight Web).  
  
## <a name="cause"></a>Causa  
 L'attributo di trasparenza del costruttore predefinito di una classe derivata non è critico come la trasparenza della classe di base.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Tipi e membri che hanno il <xref:System.Security.SecurityCriticalAttribute> non può essere utilizzato dal codice dell'applicazione Silverlight. I tipi e i membri critici per la sicurezza possono essere usati solo da codice attendibile nella libreria di classi .NET Framework per Silverlight. Poiché una costruzione pubblica o protetta in una classe derivata deve disporre della trasparenza uguale o superiore alla classe di base, una classe in un'applicazione non può essere derivata da una classe contrassegnata come SecurityCritical.  
  
 Per il codice di piattaforma CoreCLR, se un tipo di base ha un costruttore predefinito non trasparente pubblico o protetto quindi il tipo derivato deve rispettare le regole di ereditarietà del costruttore predefinito. Il tipo derivato deve inoltre avere un costruttore predefinito e tale costruttore deve essere almeno un costruttore predefinito critical del tipo di base.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere la violazione, rimuovere il tipo o deriva dal tipo di sicurezza non trasparente.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere gli avvisi da questa regola. Le violazioni di questa regola dal codice dell'applicazione comporta che caricare il tipo con CoreCLR un <xref:System.TypeLoadException>.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]  
  
### <a name="comments"></a>Commenti