---
title: 'CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3080b5a45f61010f322ed183a8b5a7c23390de33
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897418"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute
|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 L'assembly non ha un numero di versione.

## <a name="rule-description"></a>Descrizione della regola
 L'identità di un assembly è costituito da informazioni seguenti:

-   Nome assembly

-   Numero di versione

-   culture

-   Chiave pubblica (per assembly con nome sicuro).

 In [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] viene utilizzato il numero di versione per identificare in modo univoco un assembly e per stabilire associazioni a tipi in assembly con nome sicuro. Il numero di versione viene utilizzato insieme ai criteri di versione ed editore. Per impostazione predefinita, le applicazioni vengono eseguite solo con la versione di assembly con cui sono state compilate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere un numero di versione dell'assembly utilizzando il <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> attributo. Vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola per gli assembly che vengono utilizzati da terze parti, o in un ambiente di produzione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un assembly che ha il <xref:System.Reflection.AssemblyVersionAttribute> attributo applicato.

 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Vedere anche
 [Controllo delle versioni di assembly](/dotnet/framework/app-domains/assembly-versioning) [procedura: creare criteri editore](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)