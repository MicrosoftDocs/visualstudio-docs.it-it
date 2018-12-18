---
title: 'CA2114: La sicurezza del metodo deve essere un superset del tipo'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 915104e26f16005b8e0b8c4fa092be7c40d1ff7f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: La sicurezza del metodo deve essere un superset del tipo
|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo ha la sicurezza dichiarativa e uno dei relativi metodi ha la sicurezza dichiarativa per la stessa azione di sicurezza e l'azione di sicurezza non è [le richieste di collegamento](/dotnet/framework/misc/link-demands), e le autorizzazioni selezionate per il tipo non sono un sottoinsieme delle autorizzazioni controllato dal metodo.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo non può presentare sia una sicurezza dichiarativa a livello di metodo e a livello di tipo per la stessa azione. I due controlli non sono stati combinati; viene applicata solo la richiesta a livello di metodo. Ad esempio, se un tipo richiede l'autorizzazione `X`, e uno dei relativi metodi richiede l'autorizzazione `Y`, codice non è necessario disporre dell'autorizzazione `X` per eseguire il metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare il codice per assicurarsi che entrambe le azioni sono obbligatori. Se sono necessarie entrambe le azioni, assicurarsi che l'azione a livello di metodo include la sicurezza specificata a livello di tipo. Ad esempio, se il tipo richiede l'autorizzazione `X`, e il relativo metodo deve anche richiedere l'autorizzazione `Y`, il metodo deve richiedere in modo esplicito `X` e `Y`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il metodo non richiede la sicurezza specificata dal tipo. Tuttavia, questo non è uno scenario comune e potrebbe indicare la necessità di una revisione della progettazione di attenzione.

## <a name="example"></a>Esempio
 L'esempio seguente usa le autorizzazioni di ambiente per illustrare i rischi di violazione di questa regola. In questo esempio, il codice dell'applicazione crea un'istanza del tipo protetto prima di negare l'autorizzazione necessaria per il tipo. In uno scenario reale di rischio, l'applicazione potrebbe richiedere un altro modo per ottenere un'istanza dell'oggetto.

 Nell'esempio seguente, la libreria richiede l'autorizzazione per un tipo di scrittura e autorizzazioni di lettura per un metodo.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example"></a>Esempio
 Il codice di applicazione seguente illustra la vulnerabilità della libreria chiamando il metodo, anche se non soddisfa il requisito di sicurezza a livello di tipo.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

 Questo esempio produce il seguente output:

 **[Tutte le autorizzazioni] Le informazioni personali: 6/16/1964 12:00:00 AM**
**[Nessuna autorizzazione di scrittura (richiesta dal tipo)] informazioni personali: 6/16/1964 12:00:00 AM**
**[read non (autorizzazione viene richiesto dalle (metodo))] non è stato possibile accedere alle informazioni personali: richiesta non riuscita.**
## <a name="see-also"></a>Vedere anche
 [Linee guida di codice sicuro](/dotnet/standard/security/secure-coding-guidelines) [le richieste di collegamento](/dotnet/framework/misc/link-demands) [dati e modellazione](/dotnet/framework/data/index)