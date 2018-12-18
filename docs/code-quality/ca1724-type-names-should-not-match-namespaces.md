---
title: 'CA1724: I nomi dei tipi non devono corrispondere gli spazi dei nomi | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f138958ce2dc83b7d258fbdb16986841e92d3484
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi
|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Category|Microsoft. naming|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un nome di tipo corrisponde a un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] spazi dei nomi in un confronto tra maiuscole e minuscole.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I nomi dei tipi non devono corrispondere ai nomi degli spazi dei nomi definiti nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. La violazione di questa regola può ridurre l'utilizzabilità della libreria.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Selezionare un nome di tipo che corrisponde al nome di un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] spazio dei nomi della libreria di classe.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Per un nuovo sviluppo, non noto possono verificarsi scenari in cui è necessario escludere un avviso da questa regola. Prima di eliminare l'avviso, valutare attentamente come potrebbero confondere gli utenti della raccolta dal nome corrispondente. Per le librerie fornite, potrebbe essere necessario escludere un avviso da questa regola.