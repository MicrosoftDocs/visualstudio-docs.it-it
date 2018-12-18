---
title: 'CA2223: La differenza tra membri non deve limitarsi al tipo restituito'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4caffc53ff99f20a0dee94990dd6f5b966f2e047
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: La differenza tra membri non deve limitarsi al tipo restituito
|||
|-|-|
|TypeName|MembersShouldDifferByMoreThanReturnType|
|CheckId|CA2223|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Due membri pubblici o protetti avere le firme sono identiche tranne che per il tipo restituito.

## <a name="rule-description"></a>Descrizione della regola
 Nonostante common language runtime consenta l'utilizzo di tipi restituiti per differenziare membri altrimenti identici, questa funzionalità non è incluso in Common Language Specification e non è una funzionalità comune dei linguaggi di programmazione .NET. Quando i membri differiscono solo per il tipo restituito, sviluppatori e gli strumenti di sviluppo potrebbero non distinguerli correttamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, è possibile modificare la progettazione dei membri in modo che sono univoci in base solo i nomi e tipi di parametro o di non esporre i membri.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente, in Microsoft intermediate language (MSIL), viene illustrato un tipo che viola questa regola. Si noti che questa regola non può essere violata utilizzando c# o Visual Basic.

```

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit ReturnTypeTest
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance int32
            AMethod(int32 x) cil managed
    {
      // Code size       6 (0x6)
      .maxstack  1
      .locals init (int32 V_0)
      IL_0000:  ldc.i4.0
      IL_0001:  stloc.0
      IL_0002:  br.s       IL_0004

      IL_0004:  ldloc.0
      IL_0005:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig instance string
            AMethod(int32 x) cil managed
    {
      // Code size       10 (0xa)
      .maxstack  1
      .locals init (string V_0)
      IL_0000:  ldstr      "test"
      IL_0005:  stloc.0
      IL_0006:  br.s       IL_0008

      IL_0008:  ldloc.0
      IL_0009:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method ReturnTypeTest::.ctor

  } // end of class ReturnTypeTest

} // end of namespace UsageLibrary

```