---
title: 'CA1412: Contrassegnare le interfacce ComSource come IDispatch'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e4c446f1838120afd1dbcdf21ce9710982d38c0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Contrassegnare le interfacce ComSource come IDispatch
|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo è contrassegnato con il <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attributo e almeno un'interfaccia specificata non è contrassegnato con il <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attributo impostato sul `InterfaceIsDispatch` valore.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> Consente di identificare le interfacce eventi che una classe espone ai client di modello COM (Component Object). Queste interfacce devono essere esposti come `InterfaceIsIDispatch` per consentire ai client COM Visual Basic 6 ricevere le notifiche degli eventi. Per impostazione predefinita, se un'interfaccia non è contrassegnata con il <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attributo, viene esposta come un'interfaccia duale.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere o modificare il <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attributo in modo che il relativo valore è impostato su InterfaceIsIDispatch per tutte le interfacce che vengono specificate con il <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe in cui una delle interfacce viola la regola.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)