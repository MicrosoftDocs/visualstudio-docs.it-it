---
title: 'CA1025: Sostituire gli argomenti ripetitivi con una matrice di parametri | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9e6142ff6670edd6eb1f4cad009b68005b27a86f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>Ca1025: Sostituire gli argomenti ripetitivi con una matrice di parametri
|||  
|-|-|  
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|  
|CheckId|CA1025|  
|Category|Microsoft. Design|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un metodo pubblico o protetto in un tipo pubblico presenta più di tre parametri e i relativi ultimi tre parametri sono dello stesso tipo.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Utilizzare una matrice di parametri anziché argomenti ripetuti quando il numero esatto di argomenti e gli argomenti variabili sono dello stesso tipo oppure possono essere passati come lo stesso tipo. Ad esempio, il <xref:System.Console.WriteLine%2A> metodo fornisce un overload generico che utilizza una matrice di parametri per accettare un numero qualsiasi di <xref:System.Object> argomenti.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire gli argomenti ripetuti con una matrice di parametri.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È sempre possibile eliminare un avviso da questa regola. Tuttavia, ciò potrebbe causare problemi di usabilità.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola questa regola.  
  
 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]