---
title: 'CA2230: Utilizzare params per argomenti variabili | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3bd98c7dd1874617a8f6d6937c56c742a511f0de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Utilizzare params per argomenti variabili
|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|Category|Microsoft. Usage|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo pubblico o protetto contiene un metodo pubblico o protetto che utilizza il `VarArgs` convenzione di chiamata.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Il `VarArgs` convenzione di chiamata viene utilizzata con alcune definizioni di metodo che accettano un numero variabile di parametri. Un metodo tramite il `VarArgs` convenzione di chiamata non è specifica CLS (Common Language) conforme e potrebbe non essere accessibile tra diversi linguaggi di programmazione.  
  
 In c#, la `VarArgs` la convenzione di chiamata viene utilizzato quando l'elenco di parametri del metodo termina con il `__arglist` (parola chiave). Visual Basic non supporta il `VarArgs` convenzione di chiamata e Visual C++ consente l'utilizzo solo nel codice non gestito che utilizza l'ellisse `...` notazione.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola in c#, utilizzare il [params](/dotnet/csharp/language-reference/keywords/params) (parola chiave) anziché `__arglist`.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente mostra due metodi, uno che viola la regola e uno che soddisfa la regola.  
  
 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](/dotnet/standard/language-independence-and-language-independent-components)