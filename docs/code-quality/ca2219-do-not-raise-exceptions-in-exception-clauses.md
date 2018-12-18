---
title: 'CA2219: Non generare eccezioni in clausole di eccezione | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8c5a4ee1d4425b3967928171648453a631aea815
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Non generare eccezioni in clausole di eccezione
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|CheckId|CA2219|  
|Category|Microsoft. Usage|  
|Modifica importante|Non importante, di rilievo|  
  
## <a name="cause"></a>Causa  
 Viene generata un'eccezione da un `finally`, filtro o una clausola fault.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quando in una clausola di eccezione viene generata un'eccezione, aumenta notevolmente la difficoltà del debug.  
  
 Quando viene generata un'eccezione un `finally` o clausola fault, la nuova eccezione nasconde l'eccezione attiva, se presente. In questo modo difficili da rilevare ed eseguire il debug dell'errore originale.  
  
 Quando viene generata un'eccezione in una clausola di filtro, il runtime automaticamente intercetta l'eccezione e fa sì che il filtro restituisce false. Non è possibile indicare la differenza tra la restituzione di false e un'eccezione da parte di un filtro. Questo rende difficile rilevare e il debug degli errori nella logica del filtro.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere la violazione di questa regola, non generare in modo esplicito un'eccezione da un `finally`, filtro o una clausola fault.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso per questa regola. Non sono scenari in cui un'eccezione generata in una clausola di eccezione offre un vantaggio al codice in esecuzione.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1065: Non generare eccezioni in posizioni impreviste](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di progettazione](../code-quality/design-warnings.md)