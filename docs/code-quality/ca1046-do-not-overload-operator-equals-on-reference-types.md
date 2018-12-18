---
title: 'CA1046: Non l''overload dell''operatore di uguaglianza sui tipi di riferimento | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 87c9b1ca85eb7edaf1050da96356640b06b66e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento
|||  
|-|-|  
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo di riferimento pubblico o annidato overload dell'operatore di uguaglianza.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Per i tipi di riferimento, l'implementazione predefinita dell'operatore di uguaglianza è quasi sempre corretta. Per impostazione predefinita, i due riferimenti sono uguali solo se puntano allo stesso oggetto.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere l'implementazione dell'operatore di uguaglianza.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola quando il tipo di riferimento si comporta come un tipo di valore incorporato. Se è appropriato per eseguire l'addizione o sottrazione nelle istanze del tipo, è probabilmente corretto implementare l'operatore di uguaglianza e di escludere la violazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il comportamento predefinito quando si confrontano due riferimenti.  
  
 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## <a name="example"></a>Esempio  
 La seguente applicazione confronta alcuni riferimenti.  
  
 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 Questo esempio produce il seguente output:  
  
 **un = nuovo (2,2) e b = nuovo (2,2) sono uguali. No**  
**c e un oggetto sono uguali. Sì**  
**b e a sono = =? No**  
**c e a sono = =? Sì**   
## <a name="related-rules"></a>Regole correlate  
 [CA1013: Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators)