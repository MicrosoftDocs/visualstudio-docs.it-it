---
title: 'CA2132: I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9ec028dd4e094612736bcd1970be0b59e8a263e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
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