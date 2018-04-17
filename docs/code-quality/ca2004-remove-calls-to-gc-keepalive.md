---
title: 'CA2004: Rimuovere le chiamate a GC. KeepAlive | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d25c42202f7df2214295af4e3d1a448266cfa6cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Rimuovere le chiamate a GC.KeepAlive
|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|Category|Microsoft.Reliability|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Utilizzo di classi `SafeHandle` ma contengono ancora chiamate a `GC.KeepAlive`.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Se si desidera convertire in `SafeHandle` utilizzo, rimuovere tutte le chiamate a `GC.KeepAlive` (oggetto). In questo caso, le classi non necessario chiamare `GC.KeepAlive`, supponendo che non dispone di un finalizzatore, ma si basano su `SafeHandle` per completare l'handle del sistema operativo per loro.  Anche se il costo di lasciare in una chiamata a `GC.KeepAlive` potrebbe essere trascurabile in termini di prestazioni, la percezione che una chiamata a `GC.KeepAlive` sia necessaria o sufficiente per risolvere un problema che potrebbe non esistere più difficile il codice di durata Gestisci.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Rimuovere le chiamate a `GC.KeepAlive`.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare questo avviso solo se non è tecnicamente corretto convertire in `SafeHandle` utilizzo della classe.