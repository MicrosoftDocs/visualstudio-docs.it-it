---
title: 'CA1040: Evitare interfacce vuote | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1b2dd61f70328ed4aa8ca08c518cebf8d6abbedb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Evitare l'utilizzo di interfacce vuote
|||  
|-|-|  
|TypeName|AvoidEmptyInterfaces|  
|CheckId|CA1040|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 L'interfaccia non dichiarato alcun membro né lo implementa due o più interfacce.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Le interfacce definiscono membri che forniscono un comportamento o un contratto di utilizzo. La funzionalità descritta dall'interfaccia può essere adottata da qualsiasi tipo, indipendentemente dal punto in cui il tipo è visualizzato nella gerarchia di ereditarietà. Un tipo implementa un'interfaccia fornendo implementazioni per i membri dell'interfaccia. Un'interfaccia vuota non definisce alcun membro. Pertanto, non definisce un contratto che può essere implementato.  
  
 Se la progettazione include vuoto interfacce utilizzato dai tipi si prevede l'implementazione, probabilmente si utilizza un'interfaccia come marcatore o come un modo per identificare un gruppo di tipi. Se questa identificazione si verifica in fase di esecuzione, il modo corretto a questo scopo è utilizzare un attributo personalizzato. Utilizzare la presenza o assenza dell'attributo o le proprietà dell'attributo, per identificare i tipi di destinazione. Se l'identificazione deve verificarsi in fase di compilazione, è possibile utilizzare un'interfaccia vuota.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Rimuovere l'interfaccia o aggiungervi membri. Se è utilizzato per assegnare un'etichetta di un set di tipi di interfaccia vuota, è possibile sostituire l'interfaccia con un attributo personalizzato.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola quando l'interfaccia viene utilizzata per identificare un set di tipi in fase di compilazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata un'interfaccia vuota.  
  
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]