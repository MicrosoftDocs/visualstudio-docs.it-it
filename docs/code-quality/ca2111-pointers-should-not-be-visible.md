---
title: 'CA2111: I puntatori non devono essere visibili'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc47d1ff109cf4e90191a436b95f2236b86d3333
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: I puntatori non devono essere visibili
|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un membro pubblico o protetto <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> campo non è di sola lettura.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.IntPtr> e <xref:System.UIntPtr> sono tipi di puntatore che vengono utilizzati per accedere alla memoria non gestita. Se un puntatore non è privato, interno o in sola lettura, codice dannoso può modificare il valore dell'indicatore di misura, potenzialmente consentire l'accesso a percorsi arbitrari nella memoria o causando errori dell'applicazione o del sistema.

 Se si prevede di proteggere l'accesso al tipo che contiene il campo del puntatore, vedere [CA2112: i tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Proteggere il puntatore del mouse, rendendo di sola lettura, interno o privato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola se non si utilizzano il valore dell'indicatore di misura.

## <a name="example"></a>Esempio
 Il codice seguente illustra i puntatori che violano e soddisfano la regola. Si noti che i puntatori non privati violano anche la regola [CA1051: non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>