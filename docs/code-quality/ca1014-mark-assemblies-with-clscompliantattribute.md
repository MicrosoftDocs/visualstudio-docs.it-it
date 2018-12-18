---
title: 'CA1014: Contrassegnare gli assembly con CLSCompliantAttribute'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc4d1309723fd6a7246d7e684fc91099ea841537
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Contrassegnare gli assembly con CLSCompliantAttribute
|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un assembly non ha il <xref:System.CLSCompliantAttribute?displayProperty=fullName> applicato l'attributo.

## <a name="rule-description"></a>Descrizione della regola
 In Common Language Specification (CLS) vengono definite limitazioni di denominazione, tipi di dati e regole che gli assembly devono rispettare per poter essere utilizzati tra diversi linguaggi di programmazione. Una buona progettazione devono che tutti gli assembly indicano in modo esplicito la conformità a CLS con <xref:System.CLSCompliantAttribute>. Se l'attributo non è presente in un assembly, l'assembly non è conforme.

 È possibile che un assembly contengono i tipi o membri che non sono compatibili con tipi conformi a CLS.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly. Invece di contrassegnare l'intero assembly come non conforme, è necessario determinare quali tipi o membri di tipo non sono conformi e contrassegnarli come tali. Se possibile, si deve fornire un'alternativa conforme a CLS per i membri non conformi, in modo che un vasto pubblico può accedere a tutte le funzionalità dell'assembly.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Se si desidera che l'assembly sia conforme, applicare l'attributo e impostarne il valore su `false`.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un assembly che ha il <xref:System.CLSCompliantAttribute?displayProperty=fullName> attributo applicato che lo dichiara come conforme a CLS.

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Vedere anche
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](/dotnet/standard/language-independence-and-language-independent-components)