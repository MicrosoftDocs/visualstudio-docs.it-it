---
title: 'CA1411: I metodi di registrazione COM non devono essere visibili'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1fbb8a3f9dd442e26ee18abd345d92be3f650c67
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: I metodi di registrazione COM non devono essere visibili
|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo contrassegnato con il <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attributo è visibile esternamente.

## <a name="rule-description"></a>Descrizione della regola
 Quando un assembly viene registrato con modello COM (Component Object), vengono aggiunte voci al Registro di sistema per ogni tipo nell'assembly visibile a COM. I metodi contrassegnati con il <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> e <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> gli attributi vengono chiamati durante i processi di registrazione e annullamento della registrazione, rispettivamente, per eseguire il codice utente specifico per la registrazione/annullamento della registrazione di questi tipi. Questo codice non deve essere chiamato di fuori di questi processi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'accessibilità del metodo `private` o `internal` (`Friend` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente mostra due metodi che violano la regola.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1410: I metodi di registrazione COM devono corrispondere](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Registrazione di assembly con COM](/dotnet/framework/interop/registering-assemblies-with-com) [Regasm.exe (strumento di registrazione Assembly)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)