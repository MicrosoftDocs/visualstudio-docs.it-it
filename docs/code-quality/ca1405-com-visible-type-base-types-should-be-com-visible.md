---
title: 'CA1405: I tipi di base tipo visibile a COM devono essere visibili a COM | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 86e12b30f27478ec8426dc152dbbfd784edad412
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM
|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|Category|Microsoft.Interoperability|  
|Modifica importante|DependsOnFix|  
  
## <a name="cause"></a>Causa  
 Un tipo visibile modello COM (Component Object) deriva da un tipo che non è visibile a COM.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quando un tipo visibile a COM aggiunge membri in una nuova versione, è necessario rispettare severe linee guida per evitare di interrompere l'associazione alla versione corrente dei client COM. Un tipo che non è visibile a COM presuppone che è necessario seguire queste regole di controllo delle versioni COM durante l'aggiunta di nuovi membri. Tuttavia, se visibile a COM un tipo deriva dal tipo invisibile a COM ed espone un'interfaccia di classe <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> (impostazione predefinita), tutti i membri pubblici del tipo di base (a meno che non siano specificatamente contrassegnati come COM invisibile, che sarebbe ridondante) vengono esposti a COM. Se il tipo di base aggiunge nuovi membri in una versione successiva, tutti i client COM che associano l'interfaccia della classe del tipo derivato potrebbero interrompere il funzionamento. Tipi visibili a COM devono derivare solo da tipi visibili a COM per ridurre il rischio di interrompere i client COM.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rendere invisibili i tipi visibili a COM di base o il tipo derivato COM.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola la regola.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)