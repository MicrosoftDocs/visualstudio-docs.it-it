---
title: 'CA2108: Controllare la sicurezza dichiarativa sui tipi di valori'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d07245724d70b5bc6ba69deae4311dcb2a10056
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Controllare la sicurezza dichiarativa sui tipi di valori
|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo di valore pubblico o protetto è protetto da un [dati e modellazione](/dotnet/framework/data/index) o [le richieste di collegamento](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Descrizione della regola
 Tipi di valore vengono allocati e inizializzati dai relativi costruttori predefiniti prima di eseguire altri costruttori. Se un tipo di valore è protetto da Demand o LinkDemand e il chiamante non dispone delle autorizzazioni per il controllo di sicurezza, un costruttore diverso da quello predefinito avrà esito negativo e verrà generata un'eccezione di sicurezza. Il tipo di valore non viene deallocato; si è mantenuto lo stato impostato dal costruttore predefinito. Non presupporre che un chiamante che passa un'istanza del tipo di valore disponga dell'autorizzazione per creare o accedere all'istanza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 È possibile correggere una violazione di questa regola se il controllo di sicurezza per rimuovere il tipo e controlli di sicurezza a livello di metodo utilizzare al suo posto. Si noti che la violazione di correzione in questo modo verrà impedisce ai chiamanti con autorizzazioni non adeguate di ottenere le istanze del tipo di valore. È necessario assicurarsi che un'istanza del tipo di valore, nello stato predefinito, non espongono informazioni riservate e non può essere utilizzata in modo dannoso.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se qualsiasi chiamante può ottenere le istanze del tipo di valore nello stato predefinito senza causare una minaccia alla sicurezza.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una raccolta che contiene un tipo di valore che viola questa regola. Si noti che il `StructureManager` tipo presuppone che un chiamante che passa un'istanza del tipo di valore disponga dell'autorizzazione per creare o accedere all'istanza.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example"></a>Esempio
 L'applicazione riportata di seguito illustra i punti deboli della libreria.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

 Questo esempio produce il seguente output:

 **Costruttore personalizzato struttura: richiesta non riuscita. ** 
 **Nuovi valori SecuredTypeStructure 100 100**
**nuovi valori SecuredTypeStructure 200 200**
## <a name="see-also"></a>Vedere anche
 [Le richieste di collegamento](/dotnet/framework/misc/link-demands) [dati e modellazione](/dotnet/framework/data/index)