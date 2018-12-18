---
title: "CA2139: I metodi Transparent non possono utilizzare l'attributo HandleProcessCorruptingExceptions"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f10eca96b9a55d6dfd8d5550bcf7b2d5c08a1a5b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: I metodi Transparent non possono utilizzare l'attributo HandleProcessCorruptingExceptions
|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo trasparente è contrassegnato con il <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola attiva qualsiasi metodo trasparente che tenti di gestire un'eccezione che danneggia tramite il processo di <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo. Un processo di eccezione che danneggia è una classificazione di eccezione CLR versione 4.0 di eccezioni come <xref:System.AccessViolationException>. L'attributo HandleProcessCorruptedStateExceptionsAttribute può essere utilizzato solo dai metodi critici per la sicurezza e sarà ignorato se applicato a un metodo trasparente. Per gestire le eccezioni che danneggiano processo, questo metodo deve diventare SecurityCritical o SecuritySafeCritical.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo o contrassegnare il metodo con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 In questo esempio, un metodo trasparente è contrassegnato con il <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo e la regola avrà esito negativo. Il metodo deve essere contrassegnato anche con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]