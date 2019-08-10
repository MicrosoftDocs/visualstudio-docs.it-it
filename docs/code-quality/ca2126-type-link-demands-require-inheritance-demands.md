---
title: 'CA2126: Per le richieste di collegamento dei tipi sono necessarie richieste di ereditarietà'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2be42519f87c3c040c1f80c80d53d490853d986e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920761"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Per le richieste di collegamento dei tipi sono necessarie richieste di ereditarietà

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Un tipo non sealed pubblico è protetto con una richiesta di collegamento, dispone di un metodo sottoponibile a override e né il tipo né il metodo sono protetti con una richiesta di ereditarietà.

## <a name="rule-description"></a>Descrizione della regola
Una richiesta di collegamento su un metodo o sul tipo dichiarante richiede che il chiamante immediato del metodo disponga dell'autorizzazione specificata. Una richiesta di ereditarietà su un metodo richiede che un metodo di override disponga dell'autorizzazione specificata. Una richiesta di ereditarietà su un tipo richiede che una classe di derivazione disponga dell'autorizzazione specificata.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, proteggere il tipo o il metodo con una richiesta di ereditarietà per la stessa autorizzazione della richiesta di collegamento.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo che viola la regola.

[!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
[!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
[!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA2108: Controllare la sicurezza dichiarativa sui tipi di valore](../code-quality/ca2108-review-declarative-security-on-value-types.md)

[CA2112 I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA2122: Non esporre indirettamente metodi con richieste di collegamento](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

[CA2123: L'override delle richieste di collegamento deve essere identico a quello di base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Richieste di collegamento](/dotnet/framework/misc/link-demands)