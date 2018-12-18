---
title: 'CA1408: Non utilizzare AutoDual ClassInterfaceType | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ad19c3fa245998d57542a5dfe1b9da0c61984626
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Non utilizzare AutoDual ClassInterfaceType
|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|Category|Microsoft.Interoperability|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo visibile modello COM (Component Object) è contrassegnato con il <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributo impostato sul `AutoDual` valore <xref:System.Runtime.InteropServices.ClassInterfaceType>.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I tipi che utilizzano un'interfaccia duale consentono l'associazione dei client a uno specifico layout di interfaccia. Eventuali modifiche apportate in una versione futura al layout del tipo o ai tipi base interromperanno l'associazione dei client COM all'interfaccia. Per impostazione predefinita, se il <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributo viene omesso, viene utilizzata un'interfaccia solo dispatch.  
  
 Se non diversamente specificato, tutti i tipi non generici pubblici sono visibili a COM. tutti i tipi generici e non pubblici non sono visibili a COM.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il valore della <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributo la `None` valore <xref:System.Runtime.InteropServices.ClassInterfaceType> e definire in modo esplicito l'interfaccia.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola a meno che non si è certi che il layout del tipo e i relativi tipi di base non verrà modificato in una versione futura.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata una classe che viola la regola e una nuova dichiarazione della classe per utilizzare un'interfaccia esplicita.  
  
 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1403: I tipi layout automatici non devono essere visibili a COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: Contrassegnare le interfacce ComSource come IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Qualificazione di tipi .NET per l'interoperabilità](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)