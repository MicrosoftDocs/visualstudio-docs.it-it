---
title: 'CA1506: Evitare un numero eccessivo di accoppiamenti | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d5303e147ae001d887784aa401d456d23485c453
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evitare un numero eccessivo di accoppiamenti di classi
|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|Category|Microsoft.Maintainability|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo o metodo è associata a molti altri tipi.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo.  
  
 Tipi e metodi che presentano un elevato livello di accoppiamenti di classi possono essere difficili da gestire. È consigliabile disporre di tipi e metodi che presentano accoppiamento bassa e coesione elevata.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere questa violazione, provare a riprogettare il tipo o un metodo per ridurre il numero di tipi a cui è associata.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere questo avviso quando il tipo o metodo è considerata accettabile, nonostante il numero elevato di dipendenze da altri tipi.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di manutenibilità](../code-quality/maintainability-warnings.md)   
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)