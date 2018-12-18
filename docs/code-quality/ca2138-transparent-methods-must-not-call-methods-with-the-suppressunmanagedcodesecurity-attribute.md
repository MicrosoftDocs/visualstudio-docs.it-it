---
title: "CA2138: I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 10cded476edadfa6141ec68a84d74c4d8704aa35
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity
|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo SecurityTransparent chiama un metodo contrassegnato con il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola funziona su qualsiasi metodo trasparente che chiama direttamente in codice nativo, ad esempio, utilizzando un tramite P/Invoke (PInvoke) chiamare. Metodi di interoperabilità P/Invoke e COM che sono contrassegnati con il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attributo comporterà un LinkDemand eseguito la chiamata al metodo. Poiché il codice SecurityTransparent non può soddisfare i LinkDemand, il codice non è possibile chiamare anche i metodi contrassegnati con l'attributo SuppressUnmanagedCodeSecurity o metodi della classe che è contrassegnato con l'attributo SuppressUnmanagedCodeSecurity. Il metodo avrà esito negativo, o la richiesta verrà convertita in una richiesta completa.

 Violazioni di questa regola conducono a un <xref:System.MethodAccessException> il modello di trasparenza di sicurezza di livello 2 e una richiesta completa per <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> nel modello di trasparenza di livello 1.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> degli attributi e contrassegnare il metodo con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]