---
title: 'CA1505: Evitare codice non manutenibile | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5abaaba67d3390e36c4ad792d7b95bf41be80c2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: evitare codice non manutenibile
|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|CheckId|CA1505|  
|Category|Microsoft.Maintainability|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un tipo o metodo presenta un valore di indice di gestibilità basso.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Viene calcolato l'indice di manutenibilità utilizzando le seguenti metriche: righe di codice, il volume del programma e complessità ciclomatica. Il volume del programma è una misura della difficoltà di comprensione di un tipo o metodo che è in base al numero di operatori e operandi nel codice. Complessità ciclomatica è una misura della complessità strutturale del tipo o metodo. Altre informazioni sulla metrica del codice in [misurazione della complessità e la manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
 Un indice di manutenibilità basso indica che un tipo o metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere questa violazione, riprogettare il tipo o metodo e provare a dividere il più piccoli e più mirati tipi o metodi.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere questo avviso quando un tipo o metodo è considerata accettabile nonostante le grandi dimensioni o quando il tipo o metodo non può essere divisa.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di manutenibilità](../code-quality/maintainability-warnings.md)   
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)