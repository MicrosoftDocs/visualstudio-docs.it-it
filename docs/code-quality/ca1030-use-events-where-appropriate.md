---
title: 'CA1030: Utilizzare eventi dove appropriato | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 616c79e67662407562f735f5cddd2c0bf2796797
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Utilizzare eventi dove appropriato
|||  
|-|-|  
|TypeName|UseEventsWhereAppropriate|  
|CheckId|CA1030|  
|Category|Microsoft. Design|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Nome di un metodo pubblico, protetto o privato inizia con uno dei valori seguenti:  
  
-   Componente aggiuntivo  
  
-   RemoveOn  
  
-   Incendio  
  
-   Generare  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola rileva i metodi che presentano nomi comunemente utilizzati per gli eventi. Eventi seguono il modello di progettazione osservatore o pubblicazione-sottoscrizione; vengono utilizzati quando una modifica dello stato in un oggetto deve essere comunicata ad altri oggetti. Se un metodo viene chiamato in risposta a una modifica dello stato chiaramente definita, il metodo deve essere richiamato da un gestore eventi. Gli oggetti che chiamano il metodo devono generare eventi anziché chiamare direttamente il metodo.  
  
 Alcuni esempi comuni di eventi si trovano in applicazioni con interfaccia utente in cui un'azione dell'utente, ad esempio un pulsante fa sì che un segmento di codice da eseguire. Il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modello di eventi non è limitato alle interfacce utente, deve essere utilizzata ovunque è necessario comunicare lo stato passa a uno o più oggetti.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Se il metodo viene chiamato quando cambia lo stato di un oggetto, è consigliabile valutare la modifica della progettazione di utilizzare il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modello di eventi.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola se il metodo non funziona con il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modello di eventi.