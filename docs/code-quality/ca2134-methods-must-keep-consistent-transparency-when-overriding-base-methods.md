---
title: "CA2134: I metodi devono conservare trasparenza consistente durante l'override dei metodi base"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e74eee5098b23d5e0adf94259aa6ce0b9f2f423e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: I metodi devono conservare trasparenza consistente durante l'override dei metodi base
|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Questa regola viene attivata quando un metodo contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> esegue l'override di un metodo trasparente o contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute>. La regola funziona anche quando un metodo trasparente o contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> esegue l'override di un metodo contrassegnato con un <xref:System.Security.SecurityCriticalAttribute>.

 La regola è applicata in caso di esecuzione dell'override di un metodo virtuale o di implementazione di un'interfaccia.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata sui tentativi di modificare l'accessibilità di sicurezza di un metodo ulteriormente fino alla catena di ereditarietà. Ad esempio, se un metodo virtuale in una classe di base è trasparente o critico, quindi la classe derivata deve eseguire l'override con un metodo transparent o SafeCritical. Al contrario, se virtuale è critico per la sicurezza, la classe derivata deve eseguire l'override con un metodo SecurityCritical. La stessa regola vale per l'implementazione di metodi di interfaccia.

 Regole di trasparenza vengono applicate quando il codice viene compilato anziché in fase di esecuzione tramite JIT in modo che il calcolo della trasparenza non dispone di informazioni di tipo dinamico. Pertanto, il risultato del calcolo della trasparenza deve essere in grado di determinare esclusivamente dai tipi statici compilato tramite JIT, indipendentemente dal tipo dinamico.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la trasparenza del metodo che si esegue l'override di un metodo virtuale o che implementa un'interfaccia per corrispondere la trasparenza di virtuale o il metodo di interfaccia.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere gli avvisi da questa regola. Le violazioni di questa regola comporterà un runtime <xref:System.TypeLoadException> per gli assembly che utilizzano la trasparenza di livello 2.

## <a name="examples"></a>Esempi

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>Vedere anche
 [Codice SecurityTransparent, livello 2](/dotnet/framework/misc/security-transparent-code-level-2)