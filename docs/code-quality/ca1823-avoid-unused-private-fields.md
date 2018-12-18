---
title: 'CA1823: Evitare campi privati non utilizzati | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8843db809184afee02a104b719392da75b14bec3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitare campi privati non utilizzati
|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|Category|Microsoft. Performance|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Questa regola viene segnalata quando un campo privato nel codice esiste ma non viene utilizzato da qualsiasi percorso di codice.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il campo o aggiungere codice che lo utilizza.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Rivedere i parametri non usati](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)