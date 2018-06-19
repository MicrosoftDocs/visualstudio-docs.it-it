---
title: 'CA2130: Le costanti SecurityCritical devono essere Transparent'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 999a4a15dd83db66365bc9ee3701fd3130cedeb1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914354"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Le costanti SecurityCritical devono essere Transparent
|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un campo costante o un membro di enumerazione è contrassegnato con il <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Descrizione della regola
 L'imposizione della trasparenza non viene applicata ai valori costanti perché i compilatori rendono inline valori costanti in modo che non sia richiesta alcuna ricerca in fase di esecuzione. I campi costanti devono essere trasparenti per la sicurezza in modo che i revisori del codice non suppongano che il codice trasparente non possa accedere alla costante.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l'attributo SecurityCritical dal campo o valore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Negli esempi seguenti, il valore enum `EnumWithCriticalValues.CriticalEnumValue` e la costante `CriticalConstant` genera questo avviso. Per risolvere i problemi, rimuovere il [`SecurityCritical`] attributo per renderli trasparente.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]