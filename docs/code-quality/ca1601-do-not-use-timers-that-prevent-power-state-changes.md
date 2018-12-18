---
title: 'CA1601: Non utilizzare i timer che impediscono le modifiche dello stato di alimentazione | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fb8ef82581f60cea3eb121e3d0c68fbffa82d8a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Non utilizzare i timer che impediscono le modifiche allo stato di potenza
|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Category|Microsoft.Mobility|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un timer è un intervallo impostato su cui si verificano più di una volta al secondo.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Intervallo di polling di una volta al secondo o utilizzare i timer che si verificano più frequentemente una volta al secondo. Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Impostare gli intervalli di timer in presenti meno di una volta al secondo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Questa regola deve essere eliminata solo se è richiesta l'attivazione di più di una volta al secondo il timer e le considerazioni di mobilità possono essere ignorate.