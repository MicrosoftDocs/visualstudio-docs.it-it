---
title: 'CA2117: I tipi APTCA devono estendere solo tipi di base APTCA'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d8b313f0e1c33eb5c17a291995956e62d8c597e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: I tipi APTCA devono estendere solo tipi di base APTCA

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo pubblico o protetto in un assembly con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attributo eredita dal tipo dichiarato in un assembly che non dispone dell'attributo.

## <a name="rule-description"></a>Descrizione della regola

Per impostazione predefinita, pubblici o protetti tipi negli assembly con nomi sicuri sono protetti in modo implicito da un [InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) per l'attendibilità totale. Gli assembly con nome sicuro contrassegnati con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attributo (APTCA) non dispone di questo tipo di protezione. L'attributo disabilita la richiesta di ereditarietà. Tipi esposti dichiarati in un assembly senza una richiesta di ereditarietà sono ereditabili dai tipi che non dispongono di attendibilità totale.

Quando l'attributo APTCA è presente in un assembly completamente attendibile e un tipo nell'assembly eredita da un tipo che non consente chiamanti parzialmente attendibili, è possibile una violazione della sicurezza. Se due tipi `T1` e `T2` soddisfano le condizioni seguenti, i chiamanti malintenzionati possono utilizzare il tipo `T1` per ignorare la richiesta di ereditarietà di attendibilità totale implicita che protegge `T2`:

- `T1` è un tipo pubblico dichiarato in un assembly completamente attendibile con l'attributo APTCA.

- `T1` eredita da un tipo `T2` all'esterno del relativo assembly.

- `T2`dell'assembly non ha l'attributo APTCA e, pertanto, non può essere ereditato dai tipi in assembly parzialmente attendibili.

Un tipo parzialmente attendibile `X` può ereditare da `T1`, che fornisce accesso a membri ereditati dichiarati `T2`. Poiché `T2` non hanno l'attributo APTCA, il relativo tipo derivato immediato (`T1`) deve soddisfare una richiesta di ereditarietà per l'attendibilità totale; `T1` sia totalmente attendibile e pertanto soddisfa questo controllo. Il rischio di sicurezza è perché `X` contribuisce a soddisfare la richiesta di ereditarietà che protegge `T2` dalle sottoclassi non attendibili. Per questo motivo, non tipi con l'attributo APTCA devono estendere tipi che non dispone dell'attributo.

Un altro problema di sicurezza e magari più comuni, che è il tipo derivato (`T1`) può, a causa di un errore del programmatore, esporre i membri protetti dal tipo che richiede attendibilità totale (`T2`). Quando si verifica questa esposizione, i chiamanti non attendibili accedere a informazioni che devono essere disponibili solo per tipi completamente attendibili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Se il tipo restituito dalla violazione di un assembly che non richiede l'attributo APTCA, rimuoverlo.

Se l'attributo APTCA è necessario, aggiungere il tipo di una richiesta di ereditarietà per l'attendibilità totale. La richiesta di ereditarietà protegge contro eredità da tipi non attendibili.

È possibile correggere una violazione aggiungendo l'attributo APTCA agli assembly dei tipi di base segnalati dalla violazione. Non eseguire questa operazione senza prima eseguire una revisione di sicurezza con utilizzo intensivo di tutto il codice negli assembly e tutto il codice che dipende dagli assembly.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi

Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che i membri protetti esposti dal tipo non consentano direttamente o indirettamente a chiamanti non attendibili di accedere a informazioni riservate, operazioni o risorse che possono essere utilizzate in modo distruttivo.

## <a name="example"></a>Esempio

L'esempio seguente usa due assembly e un'applicazione di test per illustrare la vulnerabilità di sicurezza rilevata da questa regola. Il primo assembly non ha l'attributo APTCA e non deve essere ereditabile dai tipi parzialmente attendibili (rappresentato da `T2` nella spiegazione precedente).

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

Il secondo assembly, rappresentato da `T1` nella discussione precedente, è completamente attendibile e consente ai chiamanti parzialmente attendibili.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

Il tipo di test, rappresentato da `X` nella discussione precedente, è in un assembly parzialmente attendibile.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Questo esempio produce il seguente output:

**Soddisfino in glen luoghi protetti 2/22/2003 12:00:00 AM!**

**Da Test: Sunny Prato**

**Soddisfino in Prato sunny 2/22/2003 12:00:00 AM!**

## <a name="related-rules"></a>Regole correlate

[CA2116: I metodi APTCA devono chiamare solo metodi APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Uso di librerie da codice parzialmente attendibile](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
