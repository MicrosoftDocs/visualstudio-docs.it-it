---
title: 'CA1410: I metodi di registrazione COM devono corrispondere | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 660524e4198a06eb6a7e3d627e28acaa721bf8c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: I metodi di registrazione COM devono corrispondere
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Category|Microsoft.Interoperability|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un tipo dichiara un metodo contrassegnato con il <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attributo ma non dichiara un metodo contrassegnato con il <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attributo, o viceversa.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Per i client modello COM (Component Object) creare un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] tipo, il tipo deve prima essere registrato. Se è disponibile, un metodo contrassegnato con il <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> attributo viene chiamato durante il processo di registrazione per l'esecuzione di codice specificato dall'utente. Un metodo corrispondente che è contrassegnato con il <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> attributo viene chiamato durante il processo di annullamento della registrazione per invertire le operazioni del metodo di registrazione.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere il metodo di annullamento della registrazione o di registrazione corrispondente.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola la regola. Il codice commentato viene illustrata la correzione per la violazione.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1411: I metodi di registrazione COM non devono essere visibili](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registrazione di assembly presso COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (strumento di registrazione di assembly)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)