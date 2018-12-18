---
title: 'CA2149: I metodi Transparent non devono effettuare chiamate nel codice nativo'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c14cfff80836ebaeb8b2d0dda2298f91e913083f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: I metodi Transparent non devono effettuare chiamate nel codice nativo
|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo chiama una funzione nativa tramite uno stub di metodo, ad esempio P/Invoke.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola funziona su qualsiasi metodo trasparente che chiama direttamente in codice nativo, ad esempio, tramite P/Invoke. Violazioni di questa regola conducono a un <xref:System.MethodAccessException> nel modello di trasparenza di livello 2 e una richiesta completa per <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> nel modello di trasparenza di livello 1.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il metodo che chiama il codice nativo con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]