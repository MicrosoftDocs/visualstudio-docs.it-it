---
title: "Avvisi di manutenibilità | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8d432dab79d5cd88d398a74c352cc9d34c8b4f2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="maintainability-warnings"></a>avvisi di manutenibilità
Avvisi di manutenibilità supportano la manutenzione di applicazioni e librerie.  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Regola|Descrizione|  
|----------|-----------------|  
|[CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante, con un conseguente errori.|  
|[CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)|Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà. Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione.|  
|[CA1502: Evitare complessità eccessiva](../code-quality/ca1502-avoid-excessive-complexity.md)|Questa regola misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali.|  
|[CA1504: Controllare i nomi dei campi fuorvianti](../code-quality/ca1504-review-misleading-field-names.md)|Il nome di un campo di istanza inizia con "s _", o il nome di un valore statico (condiviso in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) campo inizia con "m _".|  
|[CA1505: evitare codice non gestibile](../code-quality/ca1505-avoid-unmaintainable-code.md)|Un tipo o metodo presenta un valore di indice di gestibilità basso. Un indice di manutenibilità basso indica che un tipo o un metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione.|  
|[CA1506: Evitare un numero eccessivo di accoppiamenti di classi](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)