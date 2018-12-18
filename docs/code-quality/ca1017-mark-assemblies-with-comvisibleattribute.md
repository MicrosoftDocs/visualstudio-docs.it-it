---
title: 'CA1017: Contrassegnare gli assembly con ComVisibleAttribute'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 886de205e59ae7a10787dafe15f0ba726b99b465
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Contrassegnare gli assembly con ComVisibleAttribute
|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un assembly non ha il <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> applicato l'attributo.

## <a name="rule-description"></a>Descrizione della regola
 Il <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributo determina come i client COM accedono al codice gestito. In una buona progettazione gli assembly devono indicare in modo esplicito la visibilità COM. La visibilità COM può essere impostata per l'intero assembly e quindi eseguirne l'override per singoli tipi e membri dei tipi. Se l'attributo non è presente, il contenuto dell'assembly è visibile ai client COM.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly. Se non si desidera che l'assembly sia visibile ai client COM, applicare l'attributo e impostarne il valore su `false`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Se si desidera che l'assembly sia visibile, applicare l'attributo e impostarne il valore su `true`.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un assembly che ha il <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributo applicato per impedire che sia visibile ai client COM.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](/dotnet/framework/interop/index) [qualificazione di tipi .NET per l'interoperabilità](/dotnet/framework/interop/qualifying-net-types-for-interoperation)