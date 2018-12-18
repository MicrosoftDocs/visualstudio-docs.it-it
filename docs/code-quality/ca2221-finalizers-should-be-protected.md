---
title: 'CA2221: I finalizzatori devono essere protetti'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf4ee1aef9ef31dccad5a9728244aeaf79f9e6a4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: I finalizzatori devono essere protetti
|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo pubblico implementa un finalizzatore che non specifica della famiglia di accesso (protetto).

## <a name="rule-description"></a>Descrizione della regola
 I finalizzatori devono utilizzare il modificatore di accesso a livello di famiglia. Questa regola viene applicata dai compilatori di c#, Visual Basic e Visual C++.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il finalizzatore per essere accessibili a famiglia.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Questa regola non può essere violata in qualsiasi linguaggio .NET di alto livello; può essere violata se si sta scrivendo Microsoft Intermediate Language.

```
// =============== CLASS MEMBERS DECLARATION ===================
//   note that class flags, 'extends' and 'implements' clauses
//          are provided here for information only

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance void
            Finalize() cil managed
    {

      // Code size       1 (0x1)
      .maxstack  0
      IL_0000:  ret
    } // end of method FinalizeMethodNotProtected::Finalize

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method FinalizeMethodNotProtected::.ctor

  } // end of class FinalizeMethodNotProtected
} // end of namespace
```

## <a name="see-also"></a>Vedere anche
 [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)