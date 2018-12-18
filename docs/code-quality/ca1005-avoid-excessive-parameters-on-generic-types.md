---
title: 'CA1005: Evitare un eccessivo di parametri nei tipi generici | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3bbf8dae17c9f0fd257388d8520485bf1a5d6970
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Evitare un uso eccessivo di parametri nei tipi generici
|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo generico visibile esternamente contiene più di due parametri di tipo.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quanto più è alto il numero di parametri di tipo contenuti, maggiore è la difficoltà di sapere e ricordare cosa rappresenta ciascun parametro. È in genere ovvio con un parametro di tipo, come in `List<T>`e in alcuni casi con due parametri di tipo, come in `Dictionary<TKey, TValue>`. Se esistono più di due parametri di tipo, il livello di difficoltà sarà troppo elevato per la maggior parte degli utenti (ad esempio, `TooManyTypeParameters<T, K, V>` in c# o `TooManyTypeParameters(Of T, K, V)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare la struttura da utilizzare non più di due parametri di tipo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola a meno che la progettazione richieda assolutamente più di due parametri di tipo. Fornisce una sintassi che è facile da comprendere e utilizzare generics riduce il tempo necessario all'apprendimento e aumenta la frequenza di adozione di nuove librerie.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Usare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Generics](/dotnet/csharp/programming-guide/generics/index)