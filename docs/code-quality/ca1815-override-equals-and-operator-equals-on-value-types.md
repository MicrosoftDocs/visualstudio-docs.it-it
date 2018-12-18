---
title: "CA1815: Eseguire l'Override di equals e sui tipi di valore è uguale a (operatore) | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 927e13266bf308096592fb5714e1247f4b596ca8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore
|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|Category|Microsoft. Performance|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un tipo di valore pubblico non esegue l'override <xref:System.Object.Equals%2A?displayProperty=fullName>, oppure non implementa l'operatore di uguaglianza (= =). Questa regola non controlla le enumerazioni.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Per i tipi di valore, l'implementazione ereditata di <xref:System.Object.Equals%2A> utilizza la libreria Reflection e confronta il contenuto di tutti i campi. La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo. Se si prevede che gli utenti a confrontare o ordinare le istanze oppure le utilizzino come chiavi di tabelle hash, il tipo di valore deve implementare <xref:System.Object.Equals%2A>. Se il linguaggio di programmazione in uso supporta l'overload degli operatori, è necessario specificare anche un'implementazione degli operatori di uguaglianza e disuguaglianza.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, fornire un'implementazione di <xref:System.Object.Equals%2A>. Se possibile, implementare l'operatore di uguaglianza.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se le istanze del tipo di valore non verranno confrontate tra loro.  
  
## <a name="example-of-a-violation"></a>Esempio di violazione  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente viene illustrata una struttura (tipo di valore) che violano questa regola.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>Esempio di come correzione  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente consente di correggere la violazione precedente eseguendo l'override <xref:System.ValueType.Equals%2A?displayProperty=fullName> e l'implementazione degli operatori di uguaglianza (= =,! =).  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Object.Equals%2A?displayProperty=fullName>